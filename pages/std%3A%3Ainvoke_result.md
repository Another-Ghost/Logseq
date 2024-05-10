- `std::invoke_result` 是 C++17 标准中引入的一个[[模板元程序]]，用于在编译时推断给定[[可调用对象]]（例如函数、函数指针、Lambda 表达式、成员函数指针等）调用结果的类型。`std::invoke_result` 作为 [[std::result_of]] 的替代者，提供了更直观且符合现代 C++ 标准的方式来推断类型。
- ### 基本用法
	- `std::invoke_result` 使用方式如下：
	  ```cpp
	  std::invoke_result<Callable, ArgTypes...>::type
	  ```
		- **Callable** 是可调用实体的类型。
		- **ArgTypes ...** 是调用该实体时传递的参数类型。
		- **type** 是调用结果的类型。
- ### 示例
	- 以下示例展示了如何使用 `std::invoke_result` 来推断不同类型的可调用对象的返回类型：
	  ```cpp
	  #include <iostream>
	  #include <type_traits>
	  #include <functional>
	  
	  int add(int a, int b) {
	    return a + b;
	  }
	  
	  struct Foo {
	    double operator()(double a, double b) {
	        return a / b;
	    }
	  };
	  
	  int main() {
	    // 使用普通函数
	    std::cout << "Result type of 'add': ";
	    std::cout << typeid(std::invoke_result<decltype(&add), int, int>::type).name() << std::endl;
	  
	    // 使用函数对象
	    Foo foo;
	    std::cout << "Result type of 'Foo::operator()': ";
	    std::cout << typeid(std::invoke_result<decltype(foo), double, double>::type).name() << std::endl;
	  
	    // 使用Lambda表达式
	    auto lambda = [](int x) -> float { return x * 1.1f; };
	    std::cout << "Result type of 'lambda': ";
	    std::cout << typeid(std::invoke_result<decltype(lambda), int>::type).name() << std::endl;
	  
	    return 0;
	  }
	  ```
- 在这个示例中，我们用 `std::invoke_result` 来推断普通函数、函数对象和 Lambda 表达式的返回类型。
- ### 使用场景
- `std::invoke_result` 的主要使用场景包括：
	- **编译时类型检查**：在编写泛型代码时，可以使用 `std::invoke_result` 来确定某个操作的结果类型，进而进行编译时检查或进一步的类型推导。
	- **模板元编程**：在模板元编程中，`std::invoke_result` 可以帮助根据不同的输入参数和可调用对象调整程序行为。
	- **动态调用**：在某些需要根据条件动态选择函数或操作的场景中，`std::invoke_result` 提供了一种确定动态调用结果类型的方法。
- ### 注意事项
	- 如果提供的类型不是合法的可调用类型或参数与可调用对象不匹配，`std::invoke_result` 将不会有 `type` 成员。
	- 在使用 `std::invoke_result` 时，应确保包含头文件 `<type_traits>`。
	- 由于 `std::invoke_result` 仅在编译时执行，它不会产生运行时开销，但对代码的编译时间有一定影响。
- 总体而言，`std::invoke_result` 是现代 C++ 中处理类型推断的重要工具，特别适合用于复杂的模板编程和泛型编程中。