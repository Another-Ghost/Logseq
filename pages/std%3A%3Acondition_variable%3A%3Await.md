- `std::condition_variable::wait` 是 C++ 标准库中 `std::condition_variable` 类的一个成员函数，用于阻塞当前线程，直到另一个线程调用[notify_one]([[std::condition_variable]]) 或 `notify_all` 方法唤醒它。这个方法通常与互斥锁（`std::mutex`）一起使用，以等待某个条件成立。
- ### 使用方式
  `wait` 方法需要与一个 `std::unique_lock<std::mutex>` 对象一起使用，该对象在调用 `wait` 时自动释放互斥锁，并在条件变量被通知（唤醒当前线程）后再次自动获取互斥锁。这样做是为了防止在等待条件变量时产生竞态条件。
- ### 基本语法
  
  ```cpp
  condition_variable.wait(unique_lock<std::mutex>& lock);
  ```
- `lock`：一个管理 `std::mutex` 的 `std::unique_lock` 对象，当进入 `wait` 状态时，它会自动释放互斥锁，以允许其他线程获取互斥锁并修改条件状态或者调用 `notify_*` 方法来唤醒等待的线程。
- ### 示例
  
  以下是一个使用 `std::condition_variable::wait` 的简单示例：
  
  ```cpp
  #include <iostream>
  #include <thread>
  #include <mutex>
  #include <condition_variable>
  
  std::mutex mtx;
  std::condition_variable cv;
  bool ready = false;
  
  void print_id(int id) {
    std::unique_lock<std::mutex> lck(mtx);
    while (!ready) cv.wait(lck); // 等待直到 'ready' 变为 true
    std::cout << "Thread " << id << '\n';
  }
  
  void go() {
    std::lock_guard<std::mutex> lck(mtx);
    ready = true;
    cv.notify_all(); // 唤醒所有等待的线程
  }
  
  int main() {
    std::thread threads[10];
    for (int i = 0; i < 10; ++i)
        threads[i] = std::thread(print_id, i);
  
    std::cout << "10 threads ready to race...\n";
    go(); // 修改条件，并通知所有等待的线程
  
    for (auto& th : threads)
        th.join();
  
    return 0;
  }
  ```
  
  在这个示例中，主线程创建了10个工作线程，每个工作线程都会在 `ready` 变量变为 `true` 之前等待。`go` 函数修改 `ready` 变量并通过调用 `cv.notify_all()` 唤醒所有等待的线程。
- ### 注意事项
- 使用 `wait` 方法时，应该将它放在一个循环中以重新检查条件，以防止虚假唤醒（即线程被唤醒但条件未真正满足的情况）。
- `std::unique_lock<std::mutex>` 提供了必要的灵活性，允许在等待期间释放互斥锁，并在等待结束后重新获得互斥锁。
- `wait` 方法还有两个变体 `wait_for` 和 `wait_until`，它们允许线程等待直到某个条件成立或达到特定的时间点。