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
- ## 存储 Lambda 表达式
	- 在C++中，`std::function` 可以存储Lambda表达式，包括那些使用了隐式捕获（Implicit Capture）的Lambda表达式。当Lambda表达式捕获了它所在作用域中的变量时，这些变量的值或引用会被存储在Lambda对象中。`std::function` 对象则持有这个Lambda对象，包括它所捕获的所有内容。
	- ### 示例
	  
	  假设你有一个局部变量，并想在Lambda表达式中使用它，你可以这样做：
	  
	  ```cpp
	  #include <functional>
	  #include <iostream>
	  
	  int main() {
	    int value = 42;
	  
	    // 使用隐式捕获的Lambda表达式
	    auto lambda = [value]() {
	        std::cout << "The value is " << value << std::endl;
	    };
	  
	    // 存储Lambda表达式在 std::function 对象中
	    std::function<void()> func = lambda;
	  
	    // 调用 std::function 对象，间接调用Lambda表达式
	    func();  // 输出: The value is 42
	  
	    return 0;
	  }
	  ```
	  
	  在这个例子中，Lambda表达式隐式地捕获了局部变量 `value`。当这个Lambda表达式被存储到 `std::function<void()>` 类型的 `func` 中时，捕获的变量也随之存储在 `func` 中。
	- ### 注意事项
	- **捕获方式**：Lambda表达式可以通过值（`[=]`）或引用（`[&]`）捕获变量。通过值捕获的变量在Lambda表达式创建时被复制，而引用捕获的变量则保留对原变量的引用。
	- **生命周期**：确保Lambda表达式捕获的变量在 `std::function` 调用时仍然有效。特别是对于引用捕获，被捕获的变量必须在Lambda被调用时仍然存在。
	- **性能考虑**：使用 `std::function` 存储Lambda表达式引入了类型擦除和间接调用，这可能导致性能开销。对于性能敏感的应用，请考虑这一点。
	  
	  总结来说，`std::function` 是存储和使用Lambda表达式的强大工具，尤其是当Lambda表达式需要在创建它们的作用域之外被调用时。这提供了极大的灵活性，使得可以方便地传递和存储复杂的操作。
- ## 和 [[函数指针]]如何选择
	- 当你需要指向特定类型的函数，并且关心性能时，使用**函数指针**。
	- 当你需要更大的灵活性，或者要存储不仅仅是普通函数的可调用对象时，使用**`std::function`**。
-