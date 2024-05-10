- `std::unique_ptr` 是 C++11 引入的一个[[智能指针]]类型，它提供了对[[动态分配内存]]的 *独占所有权* 。这意味着 `std::unique_ptr` 指向一个对象，并且在同一时间内没有**其他智能指针**可以指向同一个对象。当 `std::unique_ptr` 被销毁时（例如，当它离开其作用域或被显式删除时），它指向的对象也会被自动销毁。
- ### 特点
  
  1. **自动内存管理**：`std::unique_ptr` 会在不再使用指向的对象时自动释放内存，帮助防止内存泄漏。
  
  2. **独占所有权**：一次只有一个 `std::unique_ptr` 可以指向一个给定的对象。这通过防止复制来保证（复制构造函数和复制赋值运算符被删除）。
  
  3. **可移动但不可复制**：尽管不能被复制，`std::unique_ptr` 可以被移动，这意味着所有权可以从一个 `std::unique_ptr` 转移到另一个。
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
- ### 通过移动语义转移所有权
  
  ```cpp
  std::unique_ptr<int> source(new int(10));
  std::unique_ptr<int> destination = std::move(source);
  // 现在 destination 拥有对象的所有权，source 为空
  ```
- > 测试用自定义析构
	- ```cpp
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
- ## 成员
- `std::unique_ptr` 是 C++11 引入的一种智能指针（smart pointer），用于管理动态分配的内存，以确保当对象不再需要时能够自动释放内存，避免内存泄漏。
- 与其他智能指针不同，`std::unique_ptr` 具有独占所有权的特性，意味着一个 `unique_ptr` 实例只能有一个所有者，不能被复制，但可以转移所有权。这种设计可以确保独占控制权，并且可以防止多个指针管理同一个内存块所导致的问题。
- `std::unique_ptr` 的常见成员包括：
	- **构造函数（Constructor）**：
		- 默认构造函数：创建一个空的 `unique_ptr`。
		- 指针构造函数：使用原生指针构造 `unique_ptr`。
		  ```cpp
		  std::unique_ptr<int> ptr1; // 空的 unique_ptr
		  std::unique_ptr<int> ptr2(new int(10)); // 指定初始值
		  ```
	- **解引用操作符（Dereference Operator）**：
	  用于访问 `unique_ptr` 所指向的对象。
	  ```cpp
	  std::cout << *ptr2; // 输出 10
	  ```
	- **箭头操作符（Arrow Operator）**：
	  用于访问 `unique_ptr` 所指向对象的成员。
	  ```cpp
	  struct MyClass {
	    int value;
	  };
	  
	  std::unique_ptr<MyClass> myPtr(new MyClass{42});
	  std::cout << myPtr->value; // 输出 42
	  ```
	- **`get()` 方法**：
	  返回 `unique_ptr` 所管理的原生指针。
	  ```cpp
	  int* rawPtr = ptr2.get(); // 获取原生指针
	  ```
	- **`release()` 方法**：
	  释放所有权，并返回所管理的原生指针。此后，`unique_ptr` 变为空。
	  ```cpp
	  int* rawPtr = ptr2.release(); // 释放所有权
	  ```
	- **`reset()` 方法**：
	  释放当前所管理的对象，并将 `unique_ptr` 设置为新的原生指针。
	  ```cpp
	  ptr2.reset(new int(20)); // 重新设置 unique_ptr
	  ```
	- **`swap()` 方法**：
	  与另一个 `unique_ptr` 交换所管理的指针。
	  ```cpp
	  std::unique_ptr<int> ptr3(new int(30));
	  ptr2.swap(ptr3); // 交换指针
	  ```
- 这些是 `std::unique_ptr` 的主要成员，它们帮助确保内存的自动管理和安全转移所有权。在多线程和复杂的 C++ 应用程序中，使用 `std::unique_ptr` 可以减少内存管理错误和数据竞争的可能性。希望这个概述对你有所帮助。如果您有其他问题，随时问我！