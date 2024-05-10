alias:: 条件变量

- `std::condition_variable` 是 C++ 标准库中用于线程同步的机制之一，它允许一个或多个线程在某个条件成立之前挂起（等待），并在该条件成立时被唤醒。`std::condition_variable` 需要与互斥锁（通常是 [[std::mutex]]）配合使用，以保证条件检查和条件变量等待操作的原子性。
- ## 成员
	- ### 构造函数和析构函数
		- **构造函数**：`std::condition_variable` 的构造函数不接受参数。
		- **析构函数**：在销毁 `std::condition_variable` 实例时，析构函数会被调用。如果在条件变量被销毁时仍有线程在等待，程序的行为是未定义的。
	- ### 成员函数
		- **`wait`**：阻塞当前线程直到条件变量被通知。`wait` 函数需要一个 `std::unique_lock<std::mutex>` 参数，当进入等待状态时，它会自动释放互斥锁，并在被唤醒时重新获得锁。
		  
		  ```cpp
		  void wait(std::unique_lock<std::mutex>& lock);
		  ```
		- **`wait_for`**：带超时的等待。阻塞当前线程直到条件变量被通知或指定的时间段已过。
		  
		  ```cpp
		  template <class Rep, class Period>
		  std::cv_status wait_for(std::unique_lock<std::mutex>& lock,
		                          const std::chrono::duration<Rep, Period>& rel_time);
		  ```
		- **`wait_until`**：带绝对时间的等待。阻塞当前线程直到条件变量被通知或到达指定的时间点。
		  
		  ```cpp
		  template <class Clock, class Duration>
		  std::cv_status wait_until(std::unique_lock<std::mutex>& lock,
		                            const std::chrono::time_point<Clock, Duration>& timeout_time);
		  ```
		- **`notify_one`**：唤醒在此条件变量上等待的一个线程。
		  
		  ```cpp
		  void notify_one() noexcept;
		  ```
		- **`notify_all`**：唤醒在此条件变量上等待的所有线程。
		  
		  ```cpp
		  void notify_all() noexcept;
		  ```
	- ### 使用注意事项
		- 在调用 `wait`, `wait_for`, 或 `wait_until` 时，当前线程会被阻塞。这些函数在内部自动释放互斥锁，并在条件满足被唤醒后再次自动获取互斥锁。
		- `wait_for` 和 `wait_until` 可以用于实现带超时的等待，它们返回一个 `std::cv_status`，该类型可以是 `std::cv_status::timeout` 或 `std::cv_status::no_timeout`，表示等待是否因超时而结束。
		- 使用 `notify_one` 或 `notify_all` 唤醒等待的线程时，建议在修改条件变量关联的条件后，并在持有锁的情况下调用这些函数，以避免唤醒和条件检查之间的竞态条件。
		- 通常将 `wait` 调用放在一个循环中，并在循环条件中检查等待的条件，这样可以处理虚假唤醒以及条件可能被其他线程改变的情况。
- ### 基本用法
  使用 `std::condition_variable` 通常涉及以下几个步骤：
  1. **等待条件（Waiting on a Condition）**：
   线程通过调用 `std::condition_variable` 的 `wait`、`wait_for` 或 `wait_until` 成员函数来等待某个条件。在等待过程中，线程会被挂起，并且互斥锁会被自动释放，以允许其他线程修改条件状态并进行通知。
  
  2. **通知（Notification）**：
   当条件成立时，另一个线程将调用 `std::condition_variable` 的 `notify_one` 或 `notify_all` 成员函数来唤醒一个或所有等待中的线程。被唤醒的线程随后将重新获取之前释放的互斥锁，并重新评估条件。
  
  3. **重新检查条件（Re-checking the Condition）**：
   因为可能存在虚假唤醒（spurious wakeup）或多个线程被同时唤醒的情况，所以在被 `notify_one` 或 `notify_all` 唤醒后，线程应该重新检查等待条件是否真正满足。
- ### 示例代码
  下面的示例演示了如何使用 `std::condition_variable` 来同步两个线程，其中一个线程等待一个条件变量，另一个线程在某个条件满足时通知等待的线程：
  ```cpp
  #include <iostream>
  #include <thread>
  #include <mutex>
  #include <condition_variable>
  
  std::mutex mtx;
  std::condition_variable cv;
  bool ready = false; // 条件变量关联的条件
  
  void print_id(int id) {
    std::unique_lock<std::mutex> lck(mtx); // 使用 unique_lock 因为它提供了更灵活的锁定和解锁操作
    while (!ready) cv.wait(lck); // 等待直到 ready 为 true
    // 打印线程 ID
    std::cout << "Thread " << id << '\n';
  }
  
  void go() {
    std::unique_lock<std::mutex> lck(mtx);
    ready = true; // 设置条件变量为 true
    cv.notify_all(); // 唤醒所有等待的线程
  }
  
  int main() {
    std::thread threads[10];
    // 创建10个线程
    for (int i = 0; i < 10; ++i)
        threads[i] = std::thread(print_id, i);
  
    std::cout << "10 threads ready to race...\n";
    go(); // 启动所有线程
  
    // 等待所有线程完成
    for (auto& th : threads) th.join();
  
    return 0;
  }
  ```
- ### 注意事项
	- 使用 `std::condition_variable` 时，必须要有一个 `std::mutex`（或其他互斥锁）来保护条件变量关联的条件，以防止竞态条件。
	- 总是在一个循环中等待条件变量，以避免虚假唤醒或条件在唤醒通知发出之前改变导致的问题。
	- 使用 `std::unique_lock<std::mutex>` 而不是 `std::lock_guard<std::mutex>` 作为锁，因为 `std::unique_lock` 提供了更灵活的锁管理能力，包括能够在 `std::condition_variable` 的 `wait` 调用中释放和重新获得互斥锁。
- `std::condition_variable` 是实现[[生产者-消费者模式]]、线程间的事件通知等多线程同步机制的强大工具。