alias:: make_shared

- `std::make_shared` 是 C++11 引入的一个函数模板，用于创建一个[[std::shared_ptr]]，这是一种智能指针，用于管理动态分配的对象，通过引用计数来自动释放对象。使用 `std::make_shared` 比直接使用 `shared_ptr` 的构造函数有几个优点：
- ### 优点
  
  1. **性能提升**：`std::make_shared` 通过一次动态分配内存，**同时为对象和其控制块（包括引用计数）分配空间**。相比之下，直接使用 `shared_ptr` 的构造函数会导致两次动态内存分配（一次为对象本身，一次为控制块），增加了开销。
  2. **异常安全**：使用 `std::make_shared` 可以提高代码的异常安全性。因为它通过单个函数调用完成对象的创建和控制块的初始化，减少了因异常导致资源泄漏的风险。
  3. **简化代码**：`std::make_shared` 使代码更简洁，无需显式调用[[new]]，代码更加易于阅读和维护。
- ### 用法
  
  ```cpp
  #include <memory>
  #include <iostream>
  
  class MyClass {
  public:
    MyClass(int value) : value_(value) {
        std::cout << "MyClass constructed\n";
    }
    ~MyClass() {
        std::cout << "MyClass destroyed\n";
    }
    int value() const { return value_; }
  
  private:
    int value_;
  };
  
  int main() {
    // 使用 std::make_shared 创建 shared_ptr
    std::shared_ptr<MyClass> myObject = std::make_shared<MyClass>(10);
  
    std::cout << "The value is: " << myObject->value() << std::endl;
  
    // 当 myObject 离开作用域时，MyClass 实例会自动被删除
    return 0;
  }
  ```
  
  在这个例子中，`std::make_shared<MyClass>(10)` 创建了一个 `MyClass` 的实例，并初始化其 `value_` 为 10。返回的 `std::shared_ptr<MyClass>` 管理这个 `MyClass` 实例。当 `myObject` 离开作用域或被重置时，它会自动删除关联的 `MyClass` 实例，并调用其析构函数。
- ### 注意事项
  
  尽管 `std::make_shared` 有很多优点，但在某些特殊情况下，直接使用 `std::shared_ptr` 的构造函数可能更合适。例如，当你需要对底层内存有更精细的控制，或者当类的析构函数是私有的或受保护的时候，直接使用 `std::shared_ptr` 可能是唯一的选择。
-