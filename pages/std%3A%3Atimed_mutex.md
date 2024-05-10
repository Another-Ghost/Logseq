- `std::timed_mutex`是C++标准库中的一种互斥锁，它提供了基本的互斥锁功能，并且还支持超时。与`std::mutex`相比，`std::timed_mutex`允许线程尝试锁定互斥锁一定时间，**在超时后若未能锁定，则线程可以选择放弃或执行其他操作**。这对于需要避免长时间等待资源的应用程序非常有用。
- ### 主要成员函数
	- `lock`：阻塞当前线程直到成功获得互斥锁。
	- `try_lock`：尝试获得互斥锁而不阻塞。如果成功获得互斥锁，则立即返回`true`；如果互斥锁当前被其他线程持有，则返回`false`。
	- `unlock`：释放互斥锁。
	- `try_lock_for`：接受一个时间段作为参数，如果在指定时间内互斥锁未被其他线程锁定，则锁定互斥锁并返回`true`；否则，在超时后返回`false`。
	- `try_lock_until`：接受一个绝对时间点作为参数，如果在指定时间点之前互斥锁未被其他线程锁定，则锁定互斥锁并返回`true`；否则，在超时后返回`false`。
- ### 使用示例
  
  ```cpp
  #include <mutex>
  #include <thread>
  #include <chrono>
  #include <iostream>
  
  std::timed_mutex mutex;
  
  void try_to_lock(int id) {
    // 尝试一段时间锁定互斥锁
    if (mutex.try_lock_for(std::chrono::milliseconds(100))) {
        std::cout << "Thread " << id << " acquired the mutex" << std::endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(100));
        mutex.unlock();
    } else {
        std::cout << "Thread " << id << " couldn't acquire the mutex" << std::endl;
    }
  }
  
  int main() {
    std::thread threads[2];
    for (int i = 0; i < 2; ++i) {
        threads[i] = std::thread(try_to_lock, i);
    }
  
    for (auto& t : threads) {
        t.join();
    }
  
    return 0;
  }
  ```
  
  在这个示例中，两个线程尝试锁定同一个`std::timed_mutex`。每个线程都会尝试最多100毫秒来获取互斥锁。如果一个线程成功获取了互斥锁，它将持有它100毫秒，然后释放。这演示了如何使用`std::timed_mutex`来避免线程因等待互斥锁而被无限期阻塞。
- ### 注意事项
- 在使用`std::timed_mutex`时要注意确保所有路径都会正确释放互斥锁，以避免死锁。
- 在某些情况下，`try_lock_for`和`try_lock_until`可能会因为系统调度、线程切换等原因导致实际等待时间比预期长。