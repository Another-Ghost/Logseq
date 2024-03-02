- `std::ref` 和 `std::cref` 是 C++11 引入的两个函数模板，它们位于 `<functional>` 头文件中。这两个函数用于创建对象的引用包装器（`std::reference_wrapper` 类的实例）。这些引用包装器允许你以值传递的方式在函数中传递引用，这在使用**标准库算法**或**线程**时特别有用，因为这些场合通常要求以值传递参数。
- ### `std::ref`
- **用途**：创建一个对象的引用包装器，允许以值的方式传递引用。
- **场景**：特别适用于需要以值传递方式传递引用给函数（比如[[std::thread]]构造函数）的场合。
- ### `std::cref`
- **用途**：创建一个对象的常量引用包装器，这意味着通过该包装器不能修改被引用的对象。
- **场景**：当你需要以值传递方式传递常量引用给函数，且不想在函数内部修改该对象时使用。
- ### 示例
  
  下面是一个使用 `std::ref` 和 `std::thread` 的示例，展示如何传递引用到线程函数中：
  
  ```cpp
  #include <iostream>
  #include <thread>
  #include <functional> // 包含 std::ref 和 std::cref
  
  void increment(int& value) {
    ++value;
  }
  
  int main() {
    int x = 0;
    // 使用 std::ref 传递 x 的引用，保证线程函数可以修改 x 的值
    std::thread t(increment, std::ref(x));
  
    t.join(); // 等待线程完成
  
    std::cout << "x = " << x << std::endl; // 输出修改后的 x 值
  
    return 0;
  }
  ```
  
  如果在上述代码中不使用 `std::ref` 直接传递 `x`，编译器将报错，因为 `std::thread` 的构造函数期望以值传递方式接收参数，直接传递 `x` 将尝试复制 `x`，而不是传递其引用。
- ### 注意事项
- 使用 `std::ref` 或 `std::cref` 时，被引用的对象必须在引用包装器使用期间保持有效，否则将导致未定义行为。
- 在需要传递引用到不能直接接受引用的函数或类模板（如某些标准库算法、`std::thread` 等）时，`std::ref` 和 `std::cref` 非常有用。
- `std::ref` 和 `std::cref` 返回的[[std::reference_wrapper]]对象可以像普通引用一样使用，支持解引用和转换为被包装类型的引用。