- `std::packaged_task`是C++标准库中的一个**模板类**，它将一个函数或[[可调用对象]]（如lambda表达式、函数指针、绑定表达式等）封装为一个[[异步任务]]。这个任务可以在不同的执行线程中运行，而`std::packaged_task`对象负责存储函数的返回值或异常（如果有的话），并使这些结果可以通过一个与之关联的[[std::future]]对象来访问。
- ### 主要特点
- **结果的异步访问**：`std::packaged_task`使调用者能够在另一个线程中执行函数，并通过`std::future`对象异步获取结果。
- **异常传递**：如果封装的函数抛出异常，`std::packaged_task`会捕获这个异常，并将其传递给与之关联的`std::future`对象，而不是让异常传播到调用线程。
- **一次性使用**：每个`std::packaged_task`对象只能执行一次。尝试多次调用会导致[[std::future_error]]异常。
- ### 使用示例
  
  ```cpp
  #include <iostream>
  #include <future>
  #include <thread>
  
  // 一个简单的函数，计算两个数的和
  int sum(int a, int b) {
    return a + b;
  }
  
  int main() {
    // 创建一个std::packaged_task<int()>对象。注意，我们使用std::bind来适配函数参数
    std::packaged_task<int()> task(std::bind(sum, 10, 20));
    
    // 获取与std::packaged_task相关联的std::future对象
    std::future<int> result = task.get_future();
    
    // 在一个新线程中执行任务
    std::thread t(std::move(task));
    t.detach(); // 分离线程，让它独立运行
    
    // 等待任务完成并获取结果
    std::cout << "The sum is: " << result.get() << std::endl;
    
    return 0;
  }
  ```
  
  在这个示例中，`std::packaged_task`封装了一个简单的求和函数。通过将任务移动到一个新线程并调用它，函数的执行与主线程异步进行。通过`std::future`对象，主线程可以安全地获取函数的返回值或捕获任何抛出的异常。
- ### 注意事项
	- 使用`std::packaged_task`时，需要确保它的生命周期足够长，或直到关联的`std::future`对象完成对结果的访问。
	- 如果`std::packaged_task`在执行前被销毁，与之关联的`std::future`对象会接收到一个[[std::future_error]]异常。
	- 由于`std::packaged_task`对象在执行后变得不可用，如果需要重复执行相同的任务，需要为每次执行创建一个新的`std::packaged_task`对象。
-