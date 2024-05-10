- 在 C++ 中，`std::condition_variable_any` 是标准库提供的一种同步原语，用于线程间的条件通信。它与 `std::condition_variable` 类似，但提供了更广泛的灵活性，因为它**可以与任何满足基本锁要求的锁一起使用**，而不仅仅是与[[std::unique_lock<std::mutex>]]。
- ### 主要特征和用法
- `std::condition_variable_any` 允许线程在某个条件未满足时阻塞，直到另一个线程修改了条件并通知 `condition_variable_any`。这使得它在需要多个线程同步访问共享数据或资源时非常有用。
- #### 主要方法
	- `wait(lock, predicate)`：阻塞当前线程直到条件变量被通知，并且`predicate`条件为真。在内部，这个函数会在等待通知时自动释放锁，并在重新唤醒时重新获得锁。
	- `notify_one()`：唤醒一个等待的线程。
	- `notify_all()`：唤醒所有等待的线程。
- ### 示例代码
- 以下示例演示了如何使用 `std::condition_variable_any` 来协调两个线程之间的工作，其中一个线程生产数据，另一个线程消费数据。
  ```cpp
  #include <iostream>
  #include <thread>
  #include <mutex>
  #include <condition_variable>
  #include <deque>
  
  std::deque<int> queue;
  std::mutex mtx;
  std::condition_variable_any cv;
  
  void producer(int n) {
    for (int i = 0; i < n; ++i) {
        std::unique_lock<std::mutex> lock(mtx);
        queue.push_back(i);
        std::cout << "Produced: " << i << std::endl;
        cv.notify_one();  // 通知一个等待的消费者
        lock.unlock();
        std::this_thread::sleep_for(std::chrono::seconds(1));  // 假设生产需要一些时间
    }
  }
  
  void consumer() {
    while (true) {
        std::unique_lock<std::mutex> lock(mtx);
        cv.wait(lock, []{ return !queue.empty(); });  // 等待直到队列非空
        int value = queue.front();
        queue.pop_front();
        std::cout << "Consumed: " << value << std::endl;
        lock.unlock();
        if (value == 9) break;  // 终止条件
    }
  }
  
  int main() {
    std::thread t1(producer, 10);
    std::thread t2(consumer);
    t1.join();
    t2.join();
    return 0;
  }
  ```
- 在这个例子中，`producer` 函数生成从 0 到 9 的数字，`consumer` 函数则消费这些数字。`std::condition_variable_any` 被用来同步这两个线程，确保消费者只在队列中有数据时才进行消费。
- ### 注意事项
	- 使用 `std::condition_variable_any` 时，必须确保在调用 `wait`、`notify_one` 或 `notify_all` 时锁已经被当前线程持有。
	- 与 `std::condition_variable` 相比，`std::condition_variable_any` 的使用更灵活，但可能带来额外的性能开销，因为它需要能够与任何类型的锁配合使用。
	- 与所有使用条件变量的场景一样，建议总是使用循环来检查条件，以避免伪唤醒问题。
- `std::condition_variable_any` 提供了一种强大的同步机制，适用于需要复杂锁管理或使用非标准锁的高级线程协调场景。