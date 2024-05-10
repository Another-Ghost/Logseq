- #C++Concurrency
- 在C++中，`std::future` 和 `std::shared_future` 是两种用于访问异步操作结果的类。它们都可以用来从[[异步任务]]（如通过 `std::async`, `std::packaged_task` 或 `std::promise` 创建的任务）获取结果。不过，这两个类在使用和功能上存在一些关键差异：
- ### `std::future`
	- **单所有权**：`std::future` 对象拥有对异步操作结果的独占访问权。**一旦结果被获取（通过 `get()` 方法），`std::future` 对象就不能再被用来访问该结果了。如果尝试第二次调用 `get()`，程序将抛出异常。**
	- **不可复制**：**`std::future` 对象不能被复制，只能被移动。**这意味着一个 `std::future` 对象的所有权可以从一个函数转移到另一个函数，但在任何时候只能有一个 `std::future` 对象指向异步操作的结果。
	- **阻塞和等待**：`std::future` 提供了 `wait()`, `wait_for()`, 和 `wait_until()` 方法，允许调用线程在结果变得可用之前阻塞等待。
- ### `std::shared_future`
	- **共享所有权**：与 `std::future` 不同，`std::shared_future` 允许多个 `std::shared_future` 对象共享对[[异步操作结果]]的访问权。这意味着结果可以被多次获取，而且从多个线程安全地访问。
	- **可复制**：`std::shared_future` 对象可以被复制，这样就可以轻松地在多个线程之间共享对异步结果的访问。
	- **重复访问**：`std::shared_future` 允许多次调用 `get()` 方法来获取异步操作的结果，而不会导致异常。每次调用 `get()` 都会返回相同的结果，而不影响[[共享状态]]。
- ### 使用场景
	- **`std::future`**：当你只需要在一个地方获取异步操作的结果，且不需要在多个线程间共享对这个结果的访问时，使用 `std::future`。这适用于大多数简单的异步任务场景。
	- **`std::shared_future`**：当你需要在程序的多个部分共享异步操作的结果，或者需要在多个线程中访问这个结果时，使用 `std::shared_future`。这对于需要多次检查异步操作结果的复杂场景特别有用。
- ### 示例
  转换 `std::future` 到 `std::shared_future`：
  ```cpp
  #include <future>
  #include <iostream>
  
  int compute() {
    // 模拟耗时操作
    return 42;
  }
  
  int main() {
    std::future<int> fut = std::async(compute);
    std::shared_future<int> shared_fut = fut.share();
  
    // 现在，shared_fut可以在多个线程中安全使用
    std::cout << "Result: " << shared_fut.get() << std::endl;
    // 可以再次安全调用get()，而对于std::future，这将是非法的
    std::cout << "Result (again): " << shared_fut.get() << std::endl;
  
    return 0;
  }
  ```
  
  通过这种方式，`std::future` 和 `std::shared_future` 提供了灵活的方法来处理异步编程中的不同需求，使得可以根据具体场景选择最合适的工具。