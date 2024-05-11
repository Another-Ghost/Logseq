- #C++keyword
- 在 C++ 中，`throw` 关键字用于引发异常。异常是在程序执行过程中发生的一些不正常情况，例如运行时错误、不合法的操作或其他不可预测的情况。通过引发异常，程序可以跳转到异常处理代码，并执行适当的清理工作或采取其他措施。
- ### 语法
  ```cpp
  throw expression;
  ```
	- `expression` 是一个表达式，通常是一个异常对象，可以是任意类型（通常是异常类的对象）。
- ### 示例
	- 以下是一个简单的示例，演示了如何使用 `throw` 关键字引发异常：
	  ```cpp
	  #include <iostream>
	  
	  void processInput(int value) {
	    if (value < 0) {
	        throw std::invalid_argument("Input value cannot be negative.");
	    }
	    std::cout << "Input value is: " << value << std::endl;
	  }
	  
	  int main() {
	    try {
	        processInput(-5);  // 传递负值，引发异常
	    } catch (const std::invalid_argument& e) {
	        std::cerr << "Invalid argument exception: " << e.what() << std::endl;
	    }
	    return 0;
	  }
	  ```
- 在这个例子中，`processInput` 函数检查输入值是否为负数，如果是，则使用 `throw` 关键字引发一个 `std::invalid_argument` 类型的异常。在 `main` 函数中，异常被 `try-catch` 块捕获，并在异常处理程序中打印错误信息。
- ### 异常处理
	- 异常处理是一种在程序中处理异常情况的机制，通常使用 `try-catch` 块来捕获和处理异常。`try` 块包含可能引发异常的代码，而 `catch` 块用于捕获并处理特定类型的异常。
	  ```cpp
	  try {
	    // 可能引发异常的代码
	  } catch (ExceptionType1& e1) {
	    // 处理 ExceptionType1 类型的异常
	  } catch (ExceptionType2& e2) {
	    // 处理 ExceptionType2 类型的异常
	  } catch (...) {
	    // 处理其他类型的异常
	  }
	  ```
	- 在 `try` 块中，如果发生了异常，则程序会跳转到匹配的 `catch` 块，处理异常并执行相应的代码。如果没有匹配的 `catch` 块，异常将继续向上层调用栈传播，直到找到合适的异常处理程序为止。
- ### 注意事项
	- 异常应该被适当地处理，以确保程序在异常情况下能够正常运行或正确地回收资源。
	- 异常应该被用于处理真正的异常情况，而不是用于控制流程或处理预期的错误。
	- 在使用自定义异常类时，最好继承自 [[std::exception]] 类，以便能够使用标准的异常处理机制来处理异常。