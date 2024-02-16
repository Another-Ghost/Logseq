- `std::atomic` 是 C++11 中引入的一个模板类，用于提供原子操作。原子操作是指在多线程环境中不可被中断的操作，确保在读取、修改、写入变量时不会被其他线程打断，从而避免[[竞态条件]]。使用 `std::atomic` 可以安全地在多个线程之间共享和修改数据，而不需要使用[[互斥锁]]。
- ### 基本用法
  
  `std::atomic` 类模板可以用于基本数据类型（如 `int`、`float`、指针等），也可以用于用户自定义的类型，前提是这些类型满足`std::atomic`对类型的要求（例如，必须是可拷贝构造的）。
  
  下面是一个使用 `std::atomic` 的简单示例：
  
  ```cpp
  #include <iostream>
  #include <atomic>
  #include <thread>
  #include <vector>
  
  std::atomic<int> counter(0); // 原子变量初始化为0
  
  void increment(int n) {
    for (int i = 0; i < n; ++i) {
        counter.fetch_add(1, std::memory_order_relaxed); // 原子地增加counter的值
    }
  }
  
  int main() {
    std::vector<std::thread> threads;
    int numThreads = 10;
    int incrementsPerThread = 100;
  
    // 创建并启动线程
    for (int i = 0; i < numThreads; ++i) {
        threads.emplace_back(increment, incrementsPerThread);
    }
  
    // 等待所有线程完成
    for (auto& t : threads) {
        t.join();
    }
  
    std::cout << "Expected: " << numThreads * incrementsPerThread << std::endl;
    std::cout << "Actual: " << counter.load() << std::endl; // 原子地读取counter的值
  
    return 0;
  }
  ```
  
  在这个示例中，`counter` 是一个全局的 `std::atomic<int>` 实例。多个线程并发执行 `increment` 函数，每个线程将 `counter` 的值原子地增加 `incrementsPerThread` 次。程序的输出展示了通过原子操作保证了数据一致性。
- ### 内存顺序
  
  `std::atomic` 提供了不同的内存顺序选项，用于在保证原子操作的同时，控制编译器和硬件的优化程度。这些选项包括：
- `std::memory_order_relaxed`：放宽内存顺序，允许重排序，但保证操作的原子性。
- `std::memory_order_acquire`：在当前操作之前的读写操作不能被重排序到当前操作之后。
- `std::memory_order_release`：当前操作之后的读写操作不能被重排序到当前操作之前。
- `std::memory_order_acq_rel`：同时具有 `acquire` 和 `release` 的效果。
- `std::memory_order_seq_cst`：顺序一致性内存顺序，是最严格的顺序，保证所有线程看到相同顺序的操作。
  
  选择合适的内存顺序可以在保证正确性的基础上提高程序性能。对于大多数用途，使用默认的 `std::memory_order_seq_cst` 已经足够安全，虽然它可能不是最高效的选项。
  
  `std::atomic` 是现代 C++ 并发编程的基础之一，提供了一种无需锁的线程安全操作共享数据的方式，对于开发高性能多线程应用至关重要。