alias:: 临界区

- [[临界区]]是在 并发编程 中用来表示一段访问[[共享资源]]（如共享文件、共享内存）的代码区域，该资源不能被多个线程（Thread）或进程（Process）同时访问的概念。在任何给定时间内，**只能有一个执行线程进入临界区执行**，以防止数据不一致或[[竞态条件]]的发生。
- 为了保证对共享资源的安全访问，需要使用同步机制来保护临界区。常见的同步机制包括[[互斥锁]]、[[信号量]]、临界区对象（Critical Section Objects in Windows programming）等。
	- **互斥锁**（Mutex）: 一种同步机制，用来防止两个线程同时访问一个共享资源。
	- **信号量**（Semaphore）: 一个更灵活的同步机制，可以允许多个线程根据信号量的计数值同时访问一个共享资源。
	- **临界区对象**（Critical Section Objects）: Windows特有的同步机制，用于控制同一进程内的线程对共享资源的访问。
- 在C++中，可以使用多种方式来保护临界区，包括使用[[std::mutex]]来创建互斥锁，或者使用[[std::lock_guard]]或[[std::unique_lock]]在作用域内自动管理锁的获取与释放，从而简化代码并减少因手动锁管理导致的错误。
  
  ```cpp
  #include <iostream>
  #include <thread>
  #include <mutex>
  
  std::mutex mtx; // 定义互斥锁
  
  void print_block(int n, char c) {
    mtx.lock(); // 进入临界区前加锁
    for (int i = 0; i < n; ++i) { std::cout << c; }
    std::cout << '\n';
    mtx.unlock(); // 离开临界区后解锁
  }
  
  int main() {
    std::thread t1(print_block, 50, '*');
    std::thread t2(print_block, 50, '$');
  
    t1.join();
    t2.join();
  
    return 0;
  }
  ```
  
  这个例子中，`mtx.lock()` 和 `mtx.unlock()` 调用保护了打印操作，确保一次只有一个线程可以进入这个临界区。这样，就避免了在控制台输出中字符交错的问题。