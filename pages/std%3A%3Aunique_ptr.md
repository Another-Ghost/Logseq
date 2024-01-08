- `std::unique_ptr` 是 C++11 引入的一个[[智能指针]]类型，它提供了对[[动态分配内存]]的 *独占所有权* 。这意味着 `std::unique_ptr` 指向一个对象，并且在同一时间内没有**其他智能指针**可以指向同一个对象。当 `std::unique_ptr` 被销毁时（例如，当它离开其作用域或被显式删除时），它指向的对象也会被自动销毁。
- ### 特点
  
  1. **自动内存管理**：`std::unique_ptr` 会在不再使用指向的对象时自动释放内存，帮助防止内存泄漏。
  
  2. **独占所有权**：一次只有一个 `std::unique_ptr` 可以指向一个给定的对象。这通过防止复制来保证（复制构造函数和复制赋值运算符被删除）。
  
  3. **可移动但不可复制**：尽管不能被复制，`std::unique_ptr` 可以被移动，这意味着所有权可以从一个 `std::unique_ptr` 转移到另一个。
  
  4. **自定义析构**：可以指定自定义的析构行为。
- ### 基本用法
  
  ```cpp
  #include <memory>
  
  void function() {
    std::unique_ptr<int> ptr(new int(10));
    // 自动管理动态分配的 int 对象
    // 不需要手动 delete
  }
  
  int main() {
    function();
    // 当 ptr 离开作用域时，它指向的 int 对象被自动销毁
    return 0;
  }
  ```
- ### 移动语义
  
  ```cpp
  std::unique_ptr<int> source(new int(10));
  std::unique_ptr<int> destination = std::move(source);
  // 现在 destination 拥有对象的所有权，source 为空
  ```
- ### 自定义析构
  
  ```cpp
  #include <memory>
  #include <iostream>
  
  struct MyObject {
    ~MyObject() {
        std::cout << "对象被销毁" << std::endl;
    }
  };
  
  int main() {
    std::unique_ptr<MyObject> ptr(new MyObject());
    // 自定义的析构函数将在这里被调用
    return 0;
  }
  ```
- ### 与 `std::shared_ptr` 的比较
- `std::unique_ptr` 用于独占所有权场景，而 `std::shared_ptr` 允许多个指针共享对同一个对象的所有权。
- `std::unique_ptr` 相较于 `std::shared_ptr` 有更小的内存占用和性能开销，因为它不需要管理引用计数。