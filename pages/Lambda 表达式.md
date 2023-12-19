alias:: Lambda

- 在C++中，Lambda表达式是一种方便编写[[匿名函数对象]]的方式。自从C++11标准引入以来，Lambda表达式已成为C++编程的一个重要特性，广泛应用于[[函数式编程]]风格、STL算法等场景。
- ### Lambda表达式的基本语法
  
  C++中的Lambda表达式通常包括以下几个部分：
  
  1. **捕获列表**（Capture Clause）：指定哪些外部变量被Lambda表达式捕获，以及捕获方式（值捕获或引用捕获）。
  2. **参数列表**（Parameter List）：类似于普通函数的参数列表。
  3. **可选的返回类型**（Return Type）：大多数情况下，返回类型可以被编译器自动推断。如果无法推断或者需要明确指定，可以使用 `-> Type` 语法。
  4. **函数体**（Function Body）：定义了Lambda表达式的执行操作。
- ### 示例
  
  ```cpp
  auto add = [](int a, int b) -> int {
    return a + b;
  };
  ```
  
  在这个例子中：
- `[]` 是捕获列表。此例中为空，表示没有捕获外部变量。
- `(int a, int b)` 是参数列表。
- `-> int` 显式指定了返回类型。在这个例子中，也可以省略返回类型，让编译器自动推断。
- `{ return a + b; }` 是函数体。
- ### 捕获列表
  
  捕获列表定义了Lambda表达式可以访问的外部变量（即定义Lambda表达式外部的变量），以及如何访问这些变量。主要有以下几种方式：
  
  1. [[值捕获]]：通过值传递的方式捕获外部变量。Lambda表达式内的变量是外部变量的副本。
  2. [[引用捕获]]：通过引用传递的方式捕获外部变量。Lambda表达式内的变量直接引用外部变量。
  3. **隐式捕获**：可以让编译器自动推断应该捕获哪些外部变量，以及捕获方式。使用 `=` 表示以值的方式捕获所有外部变量，使用 `&` 表示以引用方式捕获。
- ### 使用场景
  
  1. **与STL算法一起使用**：例如，在 `std::sort` 或 `std::find_if` 等算法中作为自定义比较或条件函数。
  2. **作为回调函数**：在需要传递一个简短的函数对象时，如线程的执行函数。
  3. **替代小型函数对象**：在需要定义小型函数对象时，使用Lambda表达式可以减少代码冗余。
- ## 实现原理
	- Lambda表达式在C++中是通过创建一个匿名类（也称为闭包类型）来实现的。每个Lambda表达式本质上都对应于一个唯一的类类型。当你编写一个Lambda表达式时，编译器会生成这个类的一个实例，这个类重载了`operator()`，使得这个对象可以像函数一样被调用。
	- ### Lambda表达式的基本结构
	  
	  Lambda表达式的基本形式如下：
	  
	  ```cpp
	  [捕获列表](参数列表) mutable -> 返回类型 { 函数体 }
	  ```
	- ### 实现机制
	  
	  1. **匿名类**：编译器为每个Lambda表达式生成一个匿名类（闭包类型）。这个类重载了`operator()`，使得其实例可以像函数一样被调用。
	  
	  2. **捕获列表**：Lambda表达式可以捕获外部作用域中的变量，这些变量以值或引用的形式被存储在匿名类的实例中。捕获列表决定了哪些外部变量被捕获以及如何捕获（按值或按引用）。
	  
	  3. **参数和返回类型**：Lambda表达式可以有参数列表和返回类型，类似于普通函数。这些被用于定义重载的`operator()`的签名。
	  
	  4. **函数体**：Lambda表达式的函数体成为重载的`operator()`的函数体。
	- ### 示例
	  
	  考虑以下Lambda表达式：
	  
	  ```cpp
	  int x = 10;
	  auto lambda = [x](int y) { return x + y; };
	  ```
	  
	  编译器大致会做如下转换：
	  
	  ```cpp
	  class UniqueLambdaClosure {
	    int captured_x;
	  public:
	    UniqueLambdaClosure(int x) : captured_x(x) {}
	  
	    int operator()(int y) const {
	        return captured_x + y;
	    }
	  };
	  
	  UniqueLambdaClosure lambda(x);
	  ```
	  
	  在这个转换中，编译器生成了一个唯一的闭包类型`UniqueLambdaClosure`，它捕获了变量`x`并重载了`operator()`。
	- ### 注意事项
	- **类型**：每个Lambda表达式的类型都是唯一的，即使它们的签名相同。
	- **捕获的生命周期**：按值捕获的变量在Lambda创建时被复制，按引用捕获的变量则保留对原始变量的引用。因此，需要注意捕获的变量的生命周期。
	- **可调用对象**：Lambda表达式是可调用对象，可以作为参数传递给接受函数指针、`std::function`或任何期望可调用对象的模板。
	  
	  Lambda表达式的这种实现方式使得它们非常灵活和强大，能够轻松地在不同的上下文中创建和使用匿名函数。
- ## C++函数式编程
	- 在C++中实现函数式编程风格主要依赖于一些关键特性，如Lambda表达式、标准模板库（STL）中的算法和函数对象。下面我将通过一个示例展示如何在C++中应用函数式编程风格。
	- ### 示例：使用STL算法和Lambda表达式
	  
	  假设我们有一个任务：给定一个整数向量，我们需要过滤出所有偶数，并将它们的值加倍，最后输出结果。在C++中，我们可以利用`std::vector`、`std::copy_if`和Lambda表达式来实现这一功能。
	  
	  ```cpp
	  #include <iostream>
	  #include <vector>
	  #include <algorithm>
	  #include <iterator>
	  
	  int main() {
	    // 初始化一个整数向量
	    std::vector<int> nums = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
	  
	    // 存储过滤和变换后的结果
	    std::vector<int> results;
	  
	    // 使用copy_if和Lambda表达式进行过滤和变换
	    std::copy_if(nums.begin(), nums.end(), std::back_inserter(results), 
	        [](int x) { return x % 2 == 0; }); // 过滤出偶数
	  
	    // 使用transform和Lambda表达式将值加倍
	    std::transform(results.begin(), results.end(), results.begin(), 
	        [](int x) { return x * 2; });
	  
	    // 输出结果
	    std::cout << "Transformed numbers: ";
	    for (int n : results) {
	        std::cout << n << " ";
	    }
	    std::cout << std::endl;
	  
	    return 0;
	  }
	  ```
	  
	  在这个示例中：
	  
	  1. 我们首先创建了一个`std::vector<int>`来存储原始的整数。
	  2. 使用`std::copy_if`结合Lambda表达式来过滤出所有的偶数。
	  3. 接着，使用`std::transform`和另一个Lambda表达式将过滤后的每个数加倍。
	  4. 最后，我们遍历并打印出变换后的结果。
	  
	  这个示例展示了如何使用C++中的STL算法和Lambda表达式来实现函数式编程风格。通过这种方式，我们可以编写出更加简洁、模块化和可读的代码。
-