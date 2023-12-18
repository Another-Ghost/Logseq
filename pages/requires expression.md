alias:: requires

- #C++20
- 在C++20中，`requires`语法用于定义概念（Concepts）以及在模板定义中作为约束条件。`requires`表达式提供了一种声明性的方法来指定模板参数必须满足的要求。它可以用于定义新的概念，或者直接在模板声明中作为约束。
- ### 定义概念
  
  使用`requires`语法定义概念时，你可以指定一系列对类型的要求，这些要求定义了类型必须支持的操作或属性。
  
  ```cpp
  template <typename T>
  concept ConceptName = requires(T a, T b) {
    // 表达式要求
    { a.someOperation(b) } -> std::same_as<ExpectedType>;
    // 其他要求...
  };
  ```
  
  在这个例子中，`ConceptName`是一个概念，它要求类型`T`必须支持名为`someOperation`的操作，并且该操作的返回类型必须是`ExpectedType`。
- ### 模板参数约束
  
  `requires`语法也可以直接用于模板函数或类的定义中，作为对模板参数的约束。
  
  ```cpp
  template <typename T>
  requires ConceptName<T>
  void function(T arg) {
    // 函数实现...
  }
  ```
  
  或者更简洁地，将概念作为模板参数列表的一部分：
  
  ```cpp
  template <ConceptName T>
  void function(T arg) {
    // 函数实现...
  }
  ```
- ### 使用`requires`表达式作为约束
  
  `requires`表达式也可以直接用在模板定义中，而不是作为一个命名概念的一部分。例如：
  
  ```cpp
  template <typename T>
  requires std::integral<T> && sizeof(T) >= 4
  void function(T arg) {
    // 函数实现...
  }
  ```
  
  在这个例子中，`requires`表达式直接指定了模板参数`T`必须是一个大小至少为4个字节的整数类型。
- ### 综合示例
  
  ```cpp
  template <typename T>
  concept Addable = requires(T a, T b) {
    { a + b } -> std::same_as<T>;
  };
  
  template <typename T>
  requires Addable<T>
  T add(T a, T b) {
    return a + b;
  }
  ```
  
  在这里，`Addable`概念检查类型`T`是否支持加法操作，并且加法的结果类型是`T`。然后，`add`函数模板使用这个概念来约束其参数类型必须满足`Addable`。
  
  `requires`语法提供了一种强大的方式来精确地指定模板参数应该满足的条件，从而使得模板代码更加清晰和可维护。