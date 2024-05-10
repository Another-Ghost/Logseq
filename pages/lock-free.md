alias:: 无锁, 无锁编程, 无锁编程模式

- 在多线程编程中，"lock-free"（无锁编程）是指一种能够在没有使用传统锁机制（如[[互斥锁]]）的情况下实现线程之间的同步的编程方法。无锁编程依赖于[[原子操作]]来管理对共享资源的访问，这样可以减少上下文切换的开销，避免[[死锁]]，并提高程序的并发性能。
- ### 特点
	- **性能提升**：通过减少锁的竞争和避免线程阻塞，无锁编程**有潜力提供比传统锁机制更好的性能**。
	- **避免死锁**：由于不使用互斥锁，无锁编程避免了死锁的风险。
	- **实现复杂**：正确实现无锁数据结构和算法通常比使用锁更复杂，需要深入理解计算机的内存模型和原子操作。
- ### 实现方法
  C++11及以上版本通过引入原子类型（如 `std::atomic` 和 `std::atomic_flag`）和原子操作，为无锁编程提供了直接的支持。
	- **`std::atomic`**：用于实现基本的无锁编程需求，比如对单个变量的原子读写。
	- **`std::atomic_flag`**：是最简单的原子类型，提供了一个布尔标志，可以用来实现自旋锁等简单的无锁同步机制。
- ### `std::atomic_flag` 示例
  `std::atomic_flag` 可以用来实现一个简单的自旋锁：
  ```cpp
  #include <atomic>
  #include <thread>
  #include <vector>
  #include <iostream>
  
  class Spinlock {
    std::atomic_flag flag = ATOMIC_FLAG_INIT;
  
  public:
    void lock() {
        while (flag.test_and_set(std::memory_order_acquire)) {
            // 自旋等待，直到flag被清除
        }
    }
  
    void unlock() {
        flag.clear(std::memory_order_release);
    }
  };
  
  Spinlock spinlock;
  
  void task(int n) {
    spinlock.lock();
    std::cout << "Task " << n << " is running\n";
    spinlock.unlock();
  }
  
  int main() {
    std::vector<std::thread> threads;
    for (int i = 0; i < 10; ++i) {
        threads.emplace_back(task, i);
    }
  
    for (auto& t : threads) {
        t.join();
    }
  
    return 0;
  }
  ```
- ### 注意事项
	- 无锁编程要求对内存模型和原子操作有深入的理解。
	- 并非所有操作都适合无锁编程。有时候，特别是在低竞争条件下，使用传统的锁可能更简单且效率更高。
	- 无锁编程的正确性验证相对困难，开发者需要仔细考虑所有可能的执行路径，确保算法的线程安全性。
- ## 无锁编程总结
	- 内存顺序模型用来**保证数据在多个线程的可见顺序**。
	  logseq.order-list-type:: number
-