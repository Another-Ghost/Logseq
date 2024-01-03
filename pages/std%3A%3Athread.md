- `std::thread` 是 C++11 中引入的一个库类，它提供了管理线程的机制。`std::thread` 允许您在程序中创建多个同时运行的线程，这是进行并行处理和多核编程的关键。
- ### 基本用法
  
  在使用 `std::thread` 时，您需要包含 `<thread>` 头文件。创建线程的基本方式是提供一个函数或可调用对象，`std::thread` 对象在构造时将启动新的线程来执行该函数或对象。
  
  ```cpp
  #include <thread>
  
  void function() {
    // 线程要执行的代码
  }
  
  int main() {
    std::thread threadObj(function);  // 创建并启动线程
    threadObj.join();  // 等待线程结束
    return 0;
  }
  ```
- ### 关键点
	- 1. **加入（Joining）和分离（Detaching）线程**：
		- 使用[[join()]]方法可以使主线程等待新创建的线程完成其任务。
		- 使用[[detach()]]方法可以让新创建的线程独立运行，这意味着它将在后台运行，主线程不会等待它完成。
	- 2. **传递参数**：
	  可以向线程函数传递参数。参数是通过值传递的，如果需要通过引用传递，则需要使用[[std::ref]]。
	  
	  ```cpp
	  void threadFunction(int x) {
	    // ...
	  }
	  
	  std::thread t(threadFunction, 10);  // 传递参数
	  ```
	- 3. **线程的可移动性（Thread Moveability）**：
	  `std::thread` 对象不能被复制，但它们是可移动的。这意味着您可以将线程的所有权从一个 `std::thread` 对象转移到另一个。
	- 4. **线程局部存储（Thread Local Storage, TLS）**：
	  使用[[thread_local]]关键字声明的变量在每个线程中都有自己的实例，这对于避免数据竞争和同步问题非常有用。
	- 5. **异常处理（Exception Handling）**：
	  如果线程函数内部发生异常，且没有在那里捕获，程序将终止。因此，应当在线程函数中妥善处理异常。
	- 6. **资源管理**：
	  一定要确保每个 `std::thread` 要么在生命周期结束前被加入（join），要么被分离（detach），否则在 `std::thread` 的析构函数中会调用 `std::terminate`，导致程序崩溃。
	  
	  `std::thread` 是 C++ 提供的强大工具，用于实现多线程编程，它使得编写并行和并发程序变得更加容易和安全。不过，正确地管理线程和线程间的同步仍然是一项挑战，需要开发者对线程的概念和并发编程有深入的理解。