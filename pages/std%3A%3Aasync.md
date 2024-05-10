- #C++Concurrency
- `std::async` 是 C++11 引入的一个高级并发编程工具，它**简化了线程的使用和管理**。通过 `std::async`，可以[[异步]]地启动任务，这意味着你可以在不同的[[线程]]中运行 函数 或 可调用对象 ，并且不必直接管理这些线程。`std::async` 返回一个[[std::future]]对象，该对象可用于稍后检索由异步任务产生的结果。
- ### 使用方式
	- `std::async` 可以与两种启动策略一起使用：
		- [[std::launch::async]]：**强制新任务在不同的线程上异步执行**。
		- `std::launch::deferred`：任务被延迟执行，直到调用其对应 `std::future` 的 `get()` 或 `wait()` 方法时，该任务才在当前线程中同步执行。
	- 如果不指定启动策略，实现将选择是立即在新线程上启动任务还是延迟执行。
- ### 示例
  以下是一个简单的示例，演示如何使用 `std::async` 异步执行一个函数：
  ```cpp
  #include <iostream>
  #include <future>
  #include <chrono>
  
  // 一个简单的函数，模拟耗时的计算任务
  int compute(int x) {
    std::this_thread::sleep_for(std::chrono::seconds(2)); // 模拟耗时操作
    return x * x;
  }
  
  int main() {
    // 异步启动任务
    std::future<int> result = std::async(std::launch::async, compute, 42);
  
    std::cout << "计算中，请等待..." << std::endl;
  
    // 获取并输出结果
    std::cout << "计算结果: " << result.get() << std::endl; // 调用get()会等待异步任务完成
  
    return 0;
  }
  ```
  
  在这个例子中，`compute` 函数被异步执行，而主线程继续执行并打印 "计算中，请等待..."。当调用 `result.get()` 时，如果 `compute` 函数还没有完成，主线程将阻塞等待直到 `compute` 完成并返回结果。
- ### 注意事项
	- 使用 `std::async` 时，如果返回的 `std::future` 对象被销毁且其关联的任务尚未开始执行，则该任务会被取消。
	- 调用 `std::future::get()` 会阻塞调用线程，直到异步任务完成，并且 `get()` 只能调用一次。
	- `std::async` 是一种高层次的并发编程工具，它隐藏了线程管理的复杂性，使得并发编程更加简单。然而，**对于需要精细控制线程行为的场景，直接使用线程或[[任务队列]]可能更合适**。
- `std::async` 与 `std::thread`、`std::future` 和 `std::promise` 一起，为 C++ 提供了强大的并发编程能力，使得开发多线程应用更加容易和安全。
-