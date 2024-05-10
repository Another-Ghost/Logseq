alias:: future

- #C++Concurrency
- `std::future` 是 C++11 引入的一个模板类，用于从[[异步任务]]中获取结果。当你启动一个异步任务（比如通过 [[std::async]]、[[std::packaged_task]] 或[[std::promise]]），这个任务可能在另一个线程或者另一个时间点执行，`std::future` 提供了一种机制来访问这个异步执行任务的结果。
- ### 主要功能和用法
	- **获取异步结果**：最主要的用途是从异步操作获取结果。当异步任务完成时，结果会存储在与 `std::future` 关联的[[共享状态]]中。通过调用 `std::future::get()` 方法可以获取这个结果，如果结果还没有准备好，调用线程将阻塞，直到结果变得可用。
	- **查询任务状态**：`std::future` 提供了 [[wait()]] 方法来等待异步操作完成，以及 [[wait_for()]] 和 `wait_until()`  方法来进行超时等待。
	- **只能移动**：`std::future` 对象不能被复制，只能被移动。这意味着一个 `std::future` 对象只能有一个所有者。
- ### 示例：使用 `std::async` 和 `std::future`
  下面是一个使用 `std::async` 启动异步任务并通过 `std::future` 获取结果的示例：
  ```cpp
  #include <iostream>
  #include <future>
  #include <chrono>
  
  // 定义一个函数，模拟耗时计算
  int compute(int x) {
    std::this_thread::sleep_for(std::chrono::seconds(2)); // 模拟耗时操作
    return x * x;
  }
  
  int main() {
    // 启动一个异步任务
    std::future<int> result = std::async(std::launch::async, compute, 10);
  
    std::cout << "等待异步任务完成..." << std::endl;
  
    // 获取异步任务的结果
    int value = result.get(); // 如果异步任务还没完成，这里会阻塞等待
  
    std::cout << "异步任务的结果是: " << value << std::endl;
  
    return 0;
  }
  ```
  
  在这个示例中，`std::async` 用于异步执行 `compute` 函数，而 `std::future` 对象 `result` 用于获取这个异步执行的结果。调用 `result.get()` 时，如果异步任务 `compute` 还没有完成，主线程将会阻塞等待直到结果变得可用。
- ### 注意事项
	- 调用 `std::future::get()` 方法会销毁[[共享状态]]中的结果，因此只能调用一次。如果需要多次访问结果，可以使用 [[std::shared_future]]。
	- 如果 `std::future` 对象被销毁，而它关联的异步任务还没有完成，那么这个异步任务将继续在后台运行，直到完成。但是，一旦 `std::future` 对象被销毁，就无法再获取任务的结果了。
	- 使用 `std::future` 和相关的异步机制可以简化多线程编程，但也需要注意正确管理线程资源和同步，避免死锁和资源竞争等问题。