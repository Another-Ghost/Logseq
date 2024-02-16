- 在 C++ 中，你可以通过构造[[std::mutex]]的实例来创建一个[[互斥锁]]，通过调用`lock()`成员函数来锁定它，通过调用`unlock()`成员函数来解锁它。
  但是，直接调用成员函数并不是推荐的做法，因为这意味着你必须记住在函数的每个代码路径出口，包括由于异常而产生的路径，都要调用`unlock()`。
  相反，标准C++库提供了[[std::lock_guard]]类模板，它为互斥锁实现了[[RAII]]；它在构造时锁定提供的互斥锁，在销毁时解锁它，确保锁定的互斥锁总是被正确地解锁。
- 下面的列表展示了如何使用std::mutex和std::lock_guard来保护一个可以被多个线程访问的列表。这两者都在头文件中声明。
  
  ```cpp
  #include <list>
  #include <mutex>
  #include <algorithm>
  std::list<int> some_list;
  std::mutex some_mutex;
  void add_to_list(int new_value)
  {
  	std::lock_guard<std::mutex> guard(some_mutex);
  	some_list.push_back(new_value);
  }
  bool list_contains(int value_to_find)
  {
  	std::lock_guard<std::mutex> guard(some_mutex);
  	return std::find(some_list.begin(),some_list.end(),value_to_find)
  		!= some_list.end();
  }
  ```
- C++17还引入了一种增强版的锁定保护，称为[[std::scoped_lock]]，所以在C++17环境中，这可能会被写成
  ``` cpp
  std::scoped_lock guard(some_mutex);
  ```
- ### 面相对象的互斥锁
- 虽然有时候使用全局变量是合适的，但在大多数情况下，我们通常会将互斥锁和受保护的数据一起放在一个**类**中，而不是使用全局变量。这是面向对象设计规则的标准应用：通过将它们放在一个类中，你明确地标记了它们的关联性，并且可以封装功能并强制保护。在这种情况下，`add_to_list`和`list_contains`函数将成为类的成员函数，互斥锁和受保护的数据都将成为类的**私有成员**，这样就更容易识别哪些代码可以访问数据，从而确定哪些代码需要锁定互斥锁。如果类的所有成员函数在访问任何其他数据成员之前都锁定互斥锁，并在完成时解锁，那么数据就能很好地得到保护，防止所有人访问。
- 但这并不完全正确，如果成员函数中的一个返回了指向受保护数据的指针或引用，那么即使所有的成员函数都以一种很好、有序的方式锁定了互斥锁，也无济于事，任何能够访问到那个指针或引用的代码现在都可以在不锁定互斥锁的情况下访问（甚至可能修改）受保护的数据。因此，用互斥锁保护数据需要仔细设计接口，以确保在访问受保护数据之前锁定互斥锁，并且没有任何后门。
- ``` cpp
  /** 意外传出受保护数据的引用 */
  class some_data
  {
  	int a;
  	std::string b;
  public:
  	void do_something();
  };
  
  class data_wrapper
  {
  private:
  	some_data data;
  	std::mutex m;
  public:
  	template<typename Function>
  	void process_data(Function func)
  	{
  		std::lock_guard<std::mutex> l(m);
  		func(data);	//传递 protected 数据到用户提供的函数
  	}
  };
  
  some_data* unprotected;
  
  void malicious_function(some_data& protected_data)
  {
  	unprotected=&protected_data;
  }
  
  data_wrapper x;
  void foo()
  {
  	x.process_data(malicious_function);
  	unprotected->do_something();
  }
  ```
- 在这个例子中，`process_data`中的代码看起来足够安全，用`std::lock_guard`很好地保护了起来，但是调用用户提供的`func`函数意味着`foo`可以传入`malicious_function`来绕过保护，并且在互斥锁未锁定的情况下调用`do_something()`。
- 从根本上说，这段代码的问题在于它没有完成你想要做的事情：标记所有访问数据结构的代码片段为互斥的。在这个案例中，它漏掉了`foo()`中调用`unprotected->do_something()`的代码。
- 然而这部分问题不是C++线程库能帮你解决的；锁定正确的互斥锁来保护你的数据是你作为程序员的责任。好的一面是，你有一个遵循的指导方针：**不要将指向受保护数据的指针和引用传递到锁的作用域之外**，无论是通过从函数返回它们、将它们存储在外部可见的内存中，还是将它们作为参数传递给用户提供的函数。
- >尽管这是尝试使用互斥锁来保护共享数据时的一个常见错误，但这远非唯一的潜在陷阱。正如你将在下一节中看到的，即使数据通过互斥锁受到保护，仍然可能发生竞态条件。