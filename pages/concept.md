- #C++20
- 在C++20中，概念（Concepts）的语法提供了一种表达模板参数约束的方法。概念基本上是对模板参数可以进行的操作或其属性的一系列要求。以下是概念定义的基本语法结构：
- ### 基本定义语法
  
  ```cpp
  template <typename T>
  concept ConceptName = /* 表达式 */;
  ```
  
  这里，`ConceptName`是概念的名称，而表达式定义了T类型必须满足的要求。
- ### 表达式要求
  
  概念的表达式可以是简单的或复杂的，包括但不限于：
- **类型特性检查**：例如，检查类型是否是整数、可默认构造等。
- **函数存在性**：检查类型T是否支持特定的函数。
- **表达式有效性**：使用`requires`子句来确保特定表达式对于类型T是有效的。
- ### 使用`requires`子句的复杂概念
  
  对于更复杂的要求，可以使用`requires`子句：
  
  ```cpp
  template <typename T>
  concept ConceptName = requires(T a, T b) {
    { a.someOperation(b) } -> std::same_as<ExpectedType>;
    // 其他要求...
  };
  ```
  
  这里，`requires`子句用于指定类型T必须支持的操作。例如，上面的概念要求类型T有一个`someOperation`函数，并且这个函数的返回类型必须是`ExpectedType`。
- ### 概念的使用
  
  定义了概念后，可以在模板定义中将其用作约束条件：
  
  ```cpp
  template <ConceptName T>
  void function(T arg) {
    // 函数实现...
  }
  ```
  
  或者在模板参数列表中使用`requires`子句：
  
  ```cpp
  template <typename T>
  requires ConceptName<T>
  void function(T arg) {
    // 函数实现...
  }
  ```
- ### 内置概念
  
  C++20还引入了许多内置概念，如`std::integral`、`std::sortable`等，这些概念涵盖了常见的类型约束，可以直接在模板定义中使用。
- ### 示例
  
  ```cpp
  #include <concepts>
  
  template <std::integral T>
  void printIntegral(T value) {
    std::cout << "Integral value: " << value << std::endl;
  }
  ```
  
  在这个例子中，`printIntegral`函数模板使用了内置概念`std::integral`来约束其参数必须是整数类型。
  
  概念使得C++模板更加强大且易于理解，它们为模板元编程提供了清晰的语义和更好的编译时错误信息。