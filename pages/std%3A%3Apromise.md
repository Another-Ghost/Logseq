- #C++Concurrency
- `std::promise` 是 C++11 引入的一个模板类，用于在某个线程中存储一个值或异常，这个值或异常稍后可以通过一个与之关联的 `std::future` 对象在另一个线程中被检索。这使得 `std::promise` 和 `std::future` 一起，成为在不同线程间传递数据的一种重要机制。
- ### 基本用法
  
  1. **创建 `std::promise` 对象**：首先，你需要创建一个 `std::promise` 对象。这个对象将被用来设置一个值或异常。
  
  2. **获取 `std::future` 对象**：通过调用 `std::promise` 对象的 `get_future()` 方法，你可以获得一个与该 `promise` 对象[[共享状态]]的[[std::future]]对象。这个 `future` 对象可以在另一个线程中用来访问 `promise` 中设置的值或异常。
  
  3. **设置值或异常**：你可以通过调用 `std::promise` 的 `set_value()` 方法来存储一个值，或者调用 `set_exception()` 方法来存储一个异常。**一旦设置了值或异常，与该 `promise` 相关联的 `future` 对象将变为[[就绪状态]]**。
- ### 示例
  以下是一个使用 `std::promise` 和 `std::future` 在不同线程间传递数据的示例：
  ```cpp
  #include <iostream>
  #include <future>
  #include <thread>
  
  void producer(std::promise<int>&& prom) {
    // 模拟耗时操作
    std::this_thread::sleep_for(std::chrono::seconds(1));
    // 设置值，该值将通过与promise关联的future对象传递
    prom.set_value(42);
  }
  
  void consumer(std::future<int>& fut) {
    // 等待并获取值
    std::cout << "Waiting for the value..." << std::endl;
    std::cout << "Value received: " << fut.get() << std::endl;
  }
  
  int main() {
    std::promise<int> prom;
    std::future<int> fut = prom.get_future();
  
    std::thread prodThread(producer, std::move(prom));
    std::thread consThread(consumer, std::ref(fut));
  
    prodThread.join();
    consThread.join();
  
    return 0;
  }
  ```
  
  在这个示例中，`producer` 函数通过 `std::promise` 对象设置了一个值，而 `consumer` 函数通过与该 `promise` 对象关联的 `std::future` 对象等待并获取这个值。注意，由于 `std::promise` 对象不能被复制，只能通过[[std::move]]来传递给生产者线程。
- ### 注意事项
- `std::promise` 对象一旦设置了值或异常，就不能再次设置。尝试这样做会导致程序抛出 `std::future_error` 异常。
- 如果 `std::promise` 对象在没有设置值或异常的情况下被销毁，与之关联的 `std::future` 对象在调用 `get()` 方法时会抛出 `std::future_error` 异常。
- `std::promise` 和 `std::future` 提供了一种安全、同步的方式来在线程间传递数据，但使用时需要注意异常处理和线程安全的问题。