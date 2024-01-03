- [[std::thread]]类中的 `joinable` 成员函数是 C++11 中引入的，用于检查线程对象是否与执行中的线程相关联，也就是说，检查线程是否可被 join。如果一个线程对象是可 join 的，那么它代表一个正在执行的线程；如果不是，那么它要么代表一个尚未开始执行的线程，要么是一个已经完成执行的线程。
- ### 使用场景
  
  1. **在调用 `join` 之前检查线程是否可 join**：
   在调用[[std::thread::join]]方法之前，最好先检查线程是否可 join。这是因为对一个不可 join 的线程调用 `join` 会导致程序抛出异常。
  
  2. **在调用 `detach` 之前检查线程是否可 join**：
   同样，在调用[[std::thread::detach]]之前检查线程是否可 join 也很重要，以确保线程可以安全地分离。
- ### 示例代码
  
  下面的示例展示了如何使用 `joinable`：
  
  ```cpp
  #include <iostream>
  #include <thread>
  
  void threadFunction() {
    // 线程的任务
  }
  
  int main() {
    std::thread t(threadFunction);
  
    if (t.joinable()) {
        std::cout << "Joining thread." << std::endl;
        t.join();  // 如果线程可 join，则 join 它
    }
  
    // 如果线程已经 join 或者从未关联过线程，这里的 t.joinable() 将返回 false
    if (!t.joinable()) {
        std::cout << "Thread is not joinable." << std::endl;
    }
  
    return 0;
  }
  ```
- ### 注意事项
- **被 `join` 过的线程**：一旦线程已经被 join，它就不再是 joinable 的。
- **被 `detach` 过的线程**：一旦线程被 detach，它也不再是 joinable 的。
- **默认构造的线程对象**：如果 `std::thread` 对象是默认构造的（即没有关联到任何线程），它也不是 joinable 的。
  
  `std::thread::joinable` 是多线程编程中的一个重要概念，它有助于确保线程的正确管理和避免资源泄漏或未定义的行为。