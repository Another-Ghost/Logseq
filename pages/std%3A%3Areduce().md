- `std::reduce` 是 C++17 中引入的一个并行归约算法，用于对一个范围内的元素进行归约操作。归约操作是将一系列值缩减为一个值的操作，例如求和、求积、找到最大值或最小值等。
- ### 函数签名
  ```cpp
  template< class ExecutionPolicy, class ForwardIt, class T, class BinaryOp >
  T reduce(ExecutionPolicy&& policy, ForwardIt first, ForwardIt last, T init, BinaryOp op);
  ```
- ### 参数
	- `ExecutionPolicy&& policy`：执行策略，可以是 `std::execution::seq`（顺序执行）、`std::execution::par`（并行执行）或 `std::execution::par_unseq`（并行且并行执行）。
	- `ForwardIt first, ForwardIt last`：范围的起始和结束迭代器，定义了要归约的元素范围。
	- `T init`：归约操作的初始值。
	- `BinaryOp op`：二元函数对象，定义了归约操作的规则。
- ### 返回值
	- 归约操作的结果值。
- ### 示例
	- 下面是一个简单的示例，演示了如何使用 `std::reduce` 对向量中的元素求和：
	  ```cpp
	  #include <iostream>
	  #include <vector>
	  #include <numeric> // 包含 std::reduce
	  
	  int main() {
	    std::vector<int> vec = {1, 2, 3, 4, 5};
	  
	    // 使用并行执行策略对向量中的元素求和
	    int sum = std::reduce(std::execution::par, vec.begin(), vec.end(), 0);
	  
	    std::cout << "Sum of elements: " << sum << std::endl;
	  
	    return 0;
	  }
	  ```
	- 在这个示例中，`std::reduce` 函数对 `vec` 向量中的元素进行并行求和操作，并将结果打印出来。
- ### 注意事项
	- `std::reduce` 函数在 C++17 中引入，并用于并行归约操作。在使用前，请确保你的编译器和标准库支持 C++17 版本。
	- 归约操作的二元函数对象 `op` 必须满足结合律，以确保在并行执行时结果的正确性。
	- 使用 `std::reduce` 函数可以有效利用多核处理器的并行性能，加速归约操作的执行。
	  <!--Converted by ToLogseq-->