- `std::function` 是 C++11 标准库的一部分，是一种泛型、[[类型擦除]]的[[函数封装器]]。它用于存储、复制和调用任何可调用的目标——无论是普通函数、[[Lambda表达式]]、[[成员函数指针]]、还是具有`operator()`的[[函数对象]]。
- ### 基本用法
  `std::function` 的基本用法是创建一个能够调用特定类型签名的函数的实例。它的模板参数是一个函数类型，包括返回类型和参数类型。
- #### 示例
  
  ```cpp
  #include <functional>
  #include <iostream>
  
  // 一个普通的函数
  void printHello() {
    std::cout << "Hello, world!" << std::endl;
  }
  
  // 一个函数对象
  class Functor {
  public:
    void operator()() {
        std::cout << "Functor called" << std::endl;
    }
  };
  
  int main() {
    // 存储一个无参、无返回值的函数
    std::function<void()> func;
  
    // 绑定到普通函数
    func = printHello;
    func(); // 输出: Hello, world!
  
    // 绑定到函数对象
    Functor functor;
    func = functor;
    func(); // 输出: Functor called
  
    // 绑定到Lambda表达式
    func = []() { std::cout << "Lambda called" << std::endl; };
    func(); // 输出: Lambda called
  
    return 0;
  }
  ```
- ### 特点和优势
  
  1. **灵活性**：`std::function` 可以存储几乎任何类型的可调用对象。
  2. **类型擦除**：使用 `std::function` 可以写出与具体函数类型无关的代码。
  3. **易用性**：简化了函数指针和函数对象的使用。
- ### 性能注意事项
  
  虽然 `std::function` 提供了极大的灵活性，但这种灵活性是以性能为代价的。`std::function` 的使用可能涉及内存分配和间接调用，这可能比直接调用函数指针或直接调用对象要慢。因此，在性能敏感的代码中，如果可调用对象的类型是已知的，直接使用函数指针或直接实例化对象可能是更好的选择。
- ### 使用场景
  
  `std::function` 在需要将函数作为参数传递、存储回调函数或者实现信号与槽机制等场景中特别有用。它是实现高级抽象、如事件驱动编程或函数式编程风格等功能的重要工具。
- ## 和 [[函数指针]]如何选择
	- 当你需要指向特定类型的函数，并且关心性能时，使用**函数指针**。
	- 当你需要更大的灵活性，或者要存储不仅仅是普通函数的可调用对象时，使用**`std::function`**。