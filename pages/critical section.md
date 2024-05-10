alias:: 临界区

- [[临界区]]是在 并发编程 中用来表示一段访问 *共享资源*（如[[共享文件]]、[[共享内存]]）的代码区域，该资源不能被多个线程（Thread）或进程（Process）同时访问的概念。在任何给定时间内，**只能有一个执行线程进入临界区执行**，以防止数据不一致或[[竞态条件]]的发生。
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
- ## [[Windows]]中的临界区
	- 在Windows操作系统中，临界区（Critical Section）是一种轻量级的同步原语，用于控制多线程对共享资源的访问。与互斥量（Mutex）相比，临界区仅在同一进程的不同线程之间提供同步，不适用于进程间同步。由于临界区是在用户模式下实现的，因此它的开销比内核模式的同步原语（如互斥量）要小。
	- ### 使用临界区
	  
	  要在Windows程序中使用临界区，你需要通过一系列的API函数来初始化、使用和删除临界区对象。下面是使用临界区的基本步骤：
	  
	  1. **初始化临界区**：使用`InitializeCriticalSection`函数初始化一个临界区对象。这个操作通常在你准备开始同步访问共享资源之前进行。
	  
	   ```cpp
	   CRITICAL_SECTION CriticalSection;
	   InitializeCriticalSection(&CriticalSection);
	   ```
	  
	  2. **进入临界区**：当一个线程想要访问受保护的共享资源时，它必须首先通过调用`EnterCriticalSection`函数来进入临界区。如果另一个线程已经在临界区内，则这个线程将被阻塞，直到临界区变为可用。
	  
	   ```cpp
	   EnterCriticalSection(&CriticalSection);
	   // 访问受保护的共享资源
	   ```
	  
	  3. **离开临界区**：一旦线程完成了对共享资源的访问，它必须调用`LeaveCriticalSection`函数来离开临界区，这样其他等待的线程才能进入临界区。
	  
	   ```cpp
	   LeaveCriticalSection(&CriticalSection);
	   ```
	  
	  4. **删除临界区**：当临界区不再需要时，应使用`DeleteCriticalSection`函数删除它，以释放系统资源。
	  
	   ```cpp
	   DeleteCriticalSection(&CriticalSection);
	   ```
	- ### 特点和优点
	- **性能**：临界区在用户态完成所有操作，避免了内核态转换的开销，因此在同一进程内同步线程时非常高效。
	- **简单易用**：相对于其他同步原语，临界区的API简单，易于使用。
	- **适用场景**：临界区适合于执行时间短且频繁的同步需求。
	- ### 注意事项
	- 临界区仅适用于同一进程内的线程同步，不能用于进程间同步。
	- 必须确保每次成功调用`EnterCriticalSection`后都与之对应地调用`LeaveCriticalSection`，以避免死锁。
	- 使用临界区时，应注意避免产生优先级反转和死锁等问题。
	  
	  临界区提供了一种高效的方式来实现线程间的同步，是Windows多线程编程中常用的同步机制之一。