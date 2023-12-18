alias:: 参数包

- 参数包用于模板编程中处理可变数量的模板参数。参数包可以是模板类型参数包或模板非类型参数包，它们使得模板能够接受任意数量和类型的参数，从而为泛型编程提供了极大的灵活性。
- ### 类型参数包
  类型参数包是一种可以接受任意数量类型参数的模板参数。这在定义泛型类或函数时非常有用。
- #### 语法
  
  ```cpp
  template <typename... Args>
  class MyClass {
    // 类定义
  };
  
  template <typename... Args>
  void myFunction(Args... args) {
    // 函数实现
  }
  ```
  
  在这些例子中，`Args`是一个类型参数包，表示可以接受任意数量和类型的参数。
- ### 非类型参数包
  非类型参数包允许模板接受任意数量的非类型参数，例如整数或指针。
- #### 语法
  
  ```cpp
  template <auto... Values>
  void myFunction() {
    // 函数实现
  }
  ```
  
  在这个例子中，`Values`是一个非类型参数包，可以接受任意数量的非类型参数。
- ### [[参数包展开]]
  在模板中使用参数包时，通常需要对其进行展开，以便对每个参数执行操作。参数包的展开可以通过递归模板调用或折叠表达式（C++17中引入）实现。
- #### [[递归]]展开
  
  ```cpp
  template <typename T>
  void print(T t) {
    std::cout << t << std::endl;
  }
  
  template <typename First, typename... Rest>
  void print(First first, Rest... rest) {
    std::cout << first << ", ";
    print(rest...);  // 递归调用
  }
  ```
  
  在这个例子中，递归函数展开了参数包。
- #### [[折叠表达式]]展开
  
  ```cpp
  template <typename... Args>
  void print(Args... args) {
    (std::cout << ... << args) << std::endl;
  }
  ```
  
  在这个例子中，使用了C++17的折叠表达式来展开参数包。
- ### 应用场景
  参数包在很多场景下非常有用，例如：
	- 创建可以接受任意数量参数的函数（如`std::make_tuple`或`std::make_unique`）。
	- 实现[[变参模板类]]，如[[元组]]（`std::tuple`）。
	- 编写通用的[[函数包装器]]或委托。
-