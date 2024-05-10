alias:: 线程安全队列

- 线程安全队列是一种在多线程环境中安全使用的队列数据结构，能够保证多个线程同时对队列进行操作时的数据一致性和完整性。在没有适当的同步机制的情况下，标准的队列（如 STL 中的 `std::queue`）在多线程操作时可能会导致数据竞争（data race）和其他并发错误。
- ### 如何实现线程安全队列
- 实现线程安全队列的常见方法包括使用互斥锁（mutexes）、读写锁（reader-writer locks）或原子操作（atomic operations）。下面是一个使用互斥锁的简单线程安全队列实现的示例：
  ```cpp
  #include <queue>
  #include <mutex>
  #include <condition_variable>
  #include <exception>
  
  template<typename T>
  class ThreadSafeQueue {
  private:
    std::queue<T> queue;
    mutable std::mutex mutex;
    std::condition_variable cond;
  
  public:
    ThreadSafeQueue() {}
    ThreadSafeQueue(const ThreadSafeQueue& other) {
        std::lock_guard<std::mutex> lock(other.mutex);
        queue = other.queue;
    }
  
    void push(T value) {
        std::lock_guard<std::mutex> lock(mutex);
        queue.push(std::move(value));
        cond.notify_one();
    }
  
    T pop() {
        std::unique_lock<std::mutex> lock(mutex);
        cond.wait(lock, [this]{ return !queue.empty(); });
        T value = std::move(queue.front());
        queue.pop();
        return value;
    }
  
    bool empty() const {
        std::lock_guard<std::mutex> lock(mutex);
        return queue.empty();
    }
  };
  ```
- ### 解释
	- **互斥锁**：保证在任意时刻只有一个线程可以访问队列。
	- **条件变量**：用于在队列为空时阻塞 `pop` 操作，直到有元素被推入队列。
	- **`pop` 操作的等待机制**：如果队列为空，`pop` 操作将阻塞，直到其他线程推入新元素并发出通知。
- 这个实现保证了在多线程环境中队列操作的线程安全性，避免了数据竞争和数据损坏。
- ### 应用
	- 线程安全队列广泛应用于需要数据交换的多线程场景，例如生产者-消费者问题、日志记录、任务调度系统等。