- `std::lock_guard` 是 C++ 标准库中的一个类模板，它提供了一种方便的[[RAII]]风格的机制来管理[[互斥锁]]的锁定和解锁操作。使用 `std::lock_guard` 可以帮助避免忘记解锁互斥锁，从而减少了死锁的风险。
- ### 基本用法
  
  当创建一个 `std::lock_guard` 对象时，它会自动锁定给定的互斥锁。当 `std::lock_guard` 对象的生命周期结束时（例如，当它离开其作用域时），它的**析构函数会自动释放互斥锁**。这样，即使在抛出异常的情况下，锁也能被正确释放，保证了锁使用的安全性。
- ### 示例代码
  
  下面是一个使用 `std::lock_guard` 的简单示例，演示了如何在多线程环境中安全地访问共享数据：
  
  ```cpp
  #include <iostream>
  #include <thread>
  #include <mutex>
  #include <vector>
  
  std::mutex mtx; // 定义一个互斥锁
  
  void print_even(int x) {
    if (x % 2 == 0) {
        std::lock_guard<std::mutex> lock(mtx); // 自动锁定
        std::cout << x << " is even.\n";
        // 当离开作用域时，`lock` 被销毁，互斥锁自动解锁
    }
  }
  
  int main() {
    std::vector<std::thread> threads;
  
    // 创建并启动10个线程
    for (int i = 0; i < 10; ++i) {
        threads.emplace_back(print_even, i);
    }
  
    // 等待所有线程完成
    for (auto& th : threads) {
        th.join();
    }
  
    return 0;
  }
  ```
  
  在上面的代码中，`print_even` 函数使用 `std::lock_guard` 来保证在打印信息时互斥锁 `mtx` 被正确管理。这保证了即使多个线程尝试同时访问标准输出，输出操作也是互斥的，避免了可能的数据竞争。
- ### 注意事项
	- `std::lock_guard` 不能显式地解锁互斥锁，它仅在析构时自动解锁。
	- 如果需要更灵活的锁管理，比如**需要在某个特定时间点手动解锁互斥锁**，可以使用[[std::unique_lock]]。
	- `std::lock_guard` 自 C++11 起就被包含在标准库中，是现代 C++ 推荐的同步机制之一。