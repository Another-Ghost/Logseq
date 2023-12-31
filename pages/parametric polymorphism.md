alias:: 参数化多态

- 参数化多态（Parametric Polymorphism）是一种编程语言特性，它允许编程者编写灵活、可重用的代码，这些代码可以操作多种类型而不是单一类型。这个概念在很多现代编程语言中都有体现，尤其是在支持泛型（Generics）的语言中，如C++的模板（Templates）、Java的泛型、C# 的泛型等。
- ### 核心概念
  
  1. **类型参数**：参数化多态允许定义时使用类型作为参数。这意味着你可以定义一个函数或数据结构，它们可以工作在多种不同的数据类型上，具体的数据类型在使用时才确定。
  2. **代码重用**：通过使用参数化多态，可以编写更通用的代码，从而增加代码的重用性。例如，一个排序函数可以被设计为对任意类型的列表进行排序，而不仅限于特定类型。
- ### 参数化多态的优势
- **类型安全**：编译时就能检查类型错误，而不是在运行时。
- **减少代码重复**：不需要为每种类型编写专门的代码。
- **增强代码的可读性和可维护性**：由于减少了重复代码，整体代码结构更加清晰。
- ### 实现方式
- **C++的模板**：允许在类和函数级别定义泛型，编译器生成具体类型的实例。
  
  ```cpp
  template <typename T>
  T max(T a, T b) {
      return a > b ? a : b;
  }
  ```
- **Java的泛型**：使用类型参数化类和方法，提供类型安全而不牺牲性能。
  
  ```java
  public <T> T max(T a, T b) {
      return a.compareTo(b) > 0 ? a : b;
  }
  ```
- **C#的泛型**：类似于Java，提供了类型参数化的类和方法。
  
  ```csharp
  public T Max<T>(T a, T b) where T : IComparable {
      return a.CompareTo(b) > 0 ? a : b;
  }
  ```
- ### 使用场景
- **集合类**：如列表、映射、队列等，可以容纳任何类型的元素。
- **算法**：如排序、搜索等，可以适用于任何类型的元素。
- **工具类**：如工厂、构建器等，可以生成和处理不同类型的对象。
  
  参数化多态是现代编程中的一个强大特性，它使得编写高度通用且类型安全的代码成为可能。