alias:: 伪唤醒

- 伪唤醒（Spurious Wakeup）是在多线程编程中使用条件变量时可能遇到的问题。它指的是线程在没有收到实际信号的情况下，错误地从等待状态（如在 `std::condition_variable` 的 [[wait]] 或 `wait_for` 调用中）唤醒。
- ### 伪唤醒的特点
	- **随机性**：伪唤醒的发生通常是随机的，不可预测。
	- **无信号产生**：线程被唤醒，但并没有相关信号或条件被显式地触发。
	- **导致错误行为**：如果不适当处理伪唤醒，可能会导致程序逻辑错误或数据不一致。
- ### 处理伪唤醒的方式
	- 在使用条件变量时，处理伪唤醒的推荐做法是在一个循环中检查一个或多个条件，以确认线程应该继续执行还是再次等待。这样可以确保即使发生伪唤醒，线程也会再次正确地等待必要的条件。
- ### 示例代码
	- 以下是使用 C++ `std::condition_variable` 和 `std::mutex` 的示例，展示了如何处理伪唤醒：
	  ```cpp
	  #include <iostream>
	  #include <thread>
	  #include <mutex>
	  #include <condition_variable>
	  
	  std::mutex mtx;
	  std::condition_variable cv;
	  bool ready = false;
	  
	  void print_id(int id) {
	    std::unique_lock<std::mutex> lock(mtx);
	    while (!ready) {  // 处理伪唤醒：使用循环来检查条件
	        cv.wait(lock);
	    }
	    std::cout << "Thread " << id << '\n';
	  }
	  
	  void go() {
	    std::unique_lock<std::mutex> lock(mtx);
	    ready = true;
	    cv.notify_all();  // 唤醒所有等待线程
	  }
	  
	  int main() {
	    std::thread threads[10];
	    // 启动 10 个线程
	    for (int i = 0; i < 10; ++i) {
	        threads[i] = std::thread(print_id, i);
	    }
	    std::cout << "10 threads ready to race...\n";
	    go();  // 放行所有线程
	  
	    for (auto& th : threads) {
	        th.join();
	    }
	    return 0;
	  }
	  ```
	- 在这个例子中，每个线程在打印其 ID 之前都会等待一个 `ready` 条件。所有线程共享这个条件，并且使用一个循环来检查这个条件是否为真，以确保即使在没有实际信号的情况下被唤醒（伪唤醒）时，线程仍然能正确地进行等待。
- ### 总结
	- 伪唤醒是条件变量在操作系统层面的一个实现细节，可能由于操作系统的线程调度策略或其他原因导致。正确处理伪唤醒的关键是使用循环来反复检查等待的条件是否满足，而不是仅在唤醒后继续执行。这种做法确保了程序的健壮性，即使在多线程环境下发生复杂的交互和竞争情况时也能正确运行。
	  <!--Converted by ToLogseq-->