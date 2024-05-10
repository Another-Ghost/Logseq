- #C++keyword
- 在 C++ 中，`typename` 关键字用于告诉编译器一个特定的名称应被视为一个类型。这在模板编程中尤为重要，尤其是涉及到模板类型参数的依赖名称。`typename` 可以用于[[模板]]代码中来指定后续的标识符是一个类型，这有助于编译器正确解析模板代码。
- ### 用途
	- **指定[[依赖类型]]名称**：在模板定义中，当需要引用一个依赖于模板参数的嵌套类型时，需要在这个类型前使用 `typename` 关键字。这是因为编译器**在解析模板代码之前**无法知道这个标识符是否表示一个类型。
	  logseq.order-list-type:: number
	- **与 `class` 在模板参数中的互换性**：在模板参数声明中，`typename` 可以与 `class` 互换使用，用以声明一个类型模板参数。
	  logseq.order-list-type:: number
- ### 示例
	- #### 用于指定依赖类型名称
	  logseq.order-list-type:: number
		- 下面的例子展示了如何在模板中使用 `typename` 来指定一个依赖于模板参数的嵌套类型：
		  ```cpp
		  template <typename T>
		  class MyClass {
		  public:
		    typename T::SubType *ptr;  // 使用 typename 指明 SubType 是一个类型
		  };
		  
		  class Contained {
		  public:
		    typedef int SubType;  // 嵌套类型定义
		  };
		  
		  int main() {
		    MyClass<Contained> myObj;  // 正确
		    myObj.ptr = nullptr;
		    return 0;
		  }
		  ```
		  在这个示例中，`MyClass<T>::SubType` 是一个依赖于模板参数 `T` 的类型，因此在声明 `ptr` 时前面必须加上 `typename`。
	- #### 在模板参数中使用 `typename`
	  logseq.order-list-type:: number
		- `typename` 也可以用于模板参数声明，与 `class` 同义：
		  ```cpp
		  template <typename T>  // 使用 typename
		  void func(T arg) {
		    // 函数体
		  }
		  
		  template <class T>  // 使用 class，与上面的声明等价
		  void func(T arg) {
		    // 函数体
		  }
		  ```