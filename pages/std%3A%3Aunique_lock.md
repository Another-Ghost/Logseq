- [[std::unique_lock]]是 C++ 标准库中的一个类模板，提供了比[[std::lock_guard]]更灵活的互斥锁管理机制。
  与 `std::lock_guard` 类似，`std::unique_lock` 也实现了[[RAII]]模式，自动管理一个[[互斥锁]]的锁定和解锁过程。
  不过，`std::unique_lock` 提供了更多的控制能力，包括 延迟锁定（deferred locking）、尝试锁定（try-locking）、条件变量支持（condition variable support）和可转移锁所有权（transferable lock ownership）等特性。
- ### 特性
	- **灵活性**：`std::unique_lock` 允许在不立即锁定互斥锁的情况下创建锁对象，也支持在其生命周期内多次锁定和解锁同一个互斥锁。
	- **条件变量支持**：与[[std::condition_variable]]配合使用时，`std::unique_lock` 能够在等待条件变量时自动解锁，条件满足后重新锁定。
	- **转移所有权**：`std::unique_lock` 对象可以被移动（move），使得锁的所有权可以在函数之间传递。
- ### 基本用法
  
  ```cpp
  #include <mutex>
  #include <thread>
  
  std::mutex mtx; // 全局互斥锁
  
  void function() {
    std::unique_lock<std::mutex> lock(mtx); // 立即锁定 mtx
    // 在这里执行线程安全的操作
    lock.unlock(); // 手动解锁
  
    // 执行一些不需要互斥锁保护的操作
  
    lock.lock(); // 再次锁定
    // 执行其他线程安全的操作
  }
  ```
- ### 使用延迟锁定
  
  ```cpp
  std::unique_lock<std::mutex> lock(mtx, std::defer_lock); // 创建未锁定的锁对象
  lock.lock(); // 显式地锁定互斥锁
  ```
- ### 尝试锁定
  
  ```cpp
  std::unique_lock<std::mutex> lock(mtx, std::try_to_lock);
  if (lock.owns_lock()) {
    // 成功获取锁
  } else {
    // 获取锁失败，可以根据逻辑决定后续操作
  }
  ```
- ### 与条件变量配合
  
  ```cpp
  std::condition_variable cv;
  bool ready = false;
  
  void worker() {
    std::unique_lock<std::mutex> lock(mtx);
    cv.wait(lock, []{ return ready; }); // 等待 ready 变为 true
    // 继续执行
  }
  
  void signal() {
    {
        std::lock_guard<std::mutex> lock(mtx);
        ready = true;
    }
    cv.notify_one(); // 通知等待的线程
  }
  ```
  
  在上面的示例中，`worker` 函数在等待条件变量时会自动释放互斥锁，一旦条件满足（`ready` 变为 `true`），互斥锁会再次被锁定，然后继续执行后续代码。
- ### 注意事项
	- 使用 `std::unique_lock` 可以提供更高的灵活性，但这也意味着更复杂的锁管理，可能会增加错误的概率。
	- 考虑到性能和资源管理的需要，应根据实际情况选择使用 `std::lock_guard` 还是 `std::unique_lock`。简单场景下优先考虑 `std::lock_guard` 以简化代码和降低错误风险。
-