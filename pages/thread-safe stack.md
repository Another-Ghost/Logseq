- ``` cpp
  #include <exception>
  
  struct empty_stack: std::exception
  {
      const char* what() const throw();
  };
  
  template<typename T>
  class threadsafe_stack
  {
  private:
      std::stack<T> data;
      mutable std::mutex m;
  
  public:
      threadsafe_stack(){}
  
      threadsafe_stack(const threadsafe_stack& other)
      {
          std::lock_guard<std::mutex> lock(other.m);
          data = other.data;
      }
  
      threadsafe_stack& operator=(const threadsafe_stack&) = delete;
  
      void push(T new_value)
      {
          std::lock_guard<std::mutex> lock(m);
          data.push(std::move(new_value)); // 1
      }
  
      std::shared_ptr<T> pop()
      {
          std::lock_guard<std::mutex> lock(m);
          if(data.empty()) throw empty_stack(); // 2
          std::shared_ptr<T> const res(
              std::make_shared<T>(std::move(data.top()))); // 3
          data.pop(); // 4
          return res;
      }
  
      void pop(T& value)
      {
          std::lock_guard<std::mutex> lock(m);
          if(data.empty()) throw empty_stack();
          value = std::move(data.top()); // 5
          data.pop(); // 6
      }
  
      bool empty() const
      {
          std::lock_guard<std::mutex> lock(m);
          return data.empty();
      }
  };
  
  ```
- 让我们依次查看每一个指导原则，并了解它们在这里是如何应用的。
- 首先，如你所见，基本的线程安全是通过在每个成员函数中对互斥锁 `m` 加锁来提供的。这确保了任何时候只有一个线程访问数据，只要每个成员函数维护数据结构的不变性，就不会有线程看到破坏的不变性。
- 其次，`empty()` 函数与任一 `pop()` 函数之间存在潜在的竞态条件，但由于 `pop()` 函数在持锁的情况下明确检查栈是否为空，这种竞态条件并不会造成问题。通过直接在调用 `pop()` 时返回弹出的数据项，你避免了使用独立的 `top()` 和 `pop()` 成员函数（如 std::stack<> 中的）可能存在的潜在竞态条件。
- 接下来，有几个可能的异常来源。锁定互斥锁可能会抛出异常，但这可能极为罕见（因为它表明互斥锁或系统资源有问题），而且它也是每个成员函数中的第一个操作。因为没有数据被修改，这是安全的。解锁互斥锁不能失败，所以总是安全的，使用 `std::lock_guard<>` 确保互斥锁永远不会保持锁定状态。
- 调用 `data.push()` 可能会抛出异常，原因可能是复制/移动数据值时抛出异常，或者无法分配足够的内存来扩展底层数据结构。无论哪种情况，`std::stack<>` 都保证这是安全的，所以这也不是问题。
- 在 `pop()` 的第一个重载中，代码本身可能会抛出 `empty_stack` 异常，但没有任何数据被修改，所以这是安全的。创建 `res` 可能会抛出异常，有几个原因：调用 `std::make_shared` 可能会抛出异常，因为它无法为新对象分配内存和内部用于引用计数的数据，或者返回的数据项的复制构造函数或移动构造函数在复制/移动到新分配的内存时可能会抛出异常。在这两种情况下，C++ 运行时和标准库确保没有内存泄漏，新对象（如果有）被正确销毁。因为你还没有修改底层栈，所以你还是安全的。调用 `data.pop()` 保证不会抛出异常，返回结果也是如此，所以这个 `pop()` 的重载是[[异常安全]]的。
- `pop()` 的第二个重载类似，除了这次是复制赋值或移动赋值操作符可能会抛出异常，而不是新对象和 `std::shared_ptr` 实例的构建。再次，你不会修改数据结构，直到调用 `data.pop()`，它仍然保证不会抛出异常，所以这个重载也是异常安全的。
- 最后，`empty()` 不修改任何数据，所以是异常安全的。
- 这里有几个可能导致死锁的机会，因为你在持有锁的情况下调用用户代码：复制构造函数或移动构造函数 $(1, 3)$ 和复制赋值或移动赋值操作符 $(5)$ ，以及可能的用户定义的 `operator new` 。如果这些函数要么调用正在插入或移除的栈上的成员函数，要么需要任何种类的锁并且在调用栈成员函数时已持有另一个锁，就有可能发生死锁。但要求栈的用户负责确保这一点是合理的；你不能合理地期望在不复制它或为它分配内存的情况下将一个项目添加到栈上或从栈上移除。
- 因为所有成员函数使用 `std::lock_guard<>` 来保护数据，所以任何数量的线程都可以安全地调用栈成员函数。唯一不安全的成员函数是构造函数和析构函数，但这不是问题；对象只能构建一次并且只能销毁一次。无论是否并发进行，在对象未完全构建或部分析构时调用成员函数都不是一个好主意。因此，用户必须确保其他线程在栈完全构建之前无法访问栈，并且必须确保所有线程在栈被销毁之前停止访问栈。
- 虽然允许多个线程并发调用成员函数是安全的，但由于使用了锁，一次只有一个线程在栈数据结构中做任何工作。这种线程的串行化可能会限制应用程序的性能，尤其是在栈上有显著争用的情况下：当一个线程在等待锁时，它不会做任何有用的工作。此外，栈不提供等待添加项目的任何方法，因此如果线程需要等待，它必须定期调用 `empty()`，或调用 `pop()` 并捕获 `empty_stack` 异常。如果需要这种场景，这种栈实现是一个糟糕的选择，因为等待的线程必须消耗宝贵的资源检查数据，或者用户必须编写外部等待和通知代码（例如，使用条件变量），这可能会使内部锁定变得不必要且浪费。第四章中的队列展示了一种将这种等待整合到数据结构本身的方式，使用数据结构内的条件变量，接下来让我们来看看那个。
-