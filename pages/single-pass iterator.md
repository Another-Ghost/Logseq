alias:: 单通迭代器

- 在 C++ 中，**单通迭代器**（Single-Pass Iterator）是一种迭代器，通常在描述输入迭代器（Input Iterator）和输出迭代器（Output Iterator）时使用的术语。这些迭代器只能保证在一个方向上进行一次迭代访问，即迭代器通过序列的操作仅保证执行一次，并且不能回退到已经访问过的元素。
- ### 特点
- 单通迭代器主要具有以下特点：
	- **单向访问**：迭代器只能向前移动（通过 `++it`），不能向后移动或重新访问已经访问过的元素。
	  logseq.order-list-type:: number
	- **单次遍历**：每个元素只能被访问一次，一旦通过迭代器访问过，就不能再次访问，除非再次从容器的开始处获取新的迭代器。
	  logseq.order-list-type:: number
	- **有限的操作**：支持的操作通常限于递增（`++`）、解引用（`*`）和赋值（`=`）。对于输入迭代器，解引用操作通常返回对应元素的常量引用；对于输出迭代器，解引用操作通常用于赋值（`*it = value`）。
	  logseq.order-list-type:: number
- ### 应用场景
	- **输入迭代器**（Input Iterator）：用于从数据源（如文件或标准输入）读取数据。例如，`std::istream_iterator` 是用于从输入流读取数据的标准迭代器。
	- **输出迭代器**（Output Iterator）：用于向目标（如容器或标准输出）写入数据。例如，`std::ostream_iterator` 是用于向输出流写入数据的标准迭代器。
- ### 示例
- 下面的示例展示了如何使用输入迭代器和输出迭代器：
  ```cpp
  #include <iostream>
  #include <iterator>
  #include <algorithm>
  #include <vector>
  
  int main() {
    // 使用 istream_iterator 读取标准输入直到 EOF
    std::vector<int> data;
    std::cout << "Enter integers (EOF to stop): ";
    std::copy(std::istream_iterator<int>(std::cin), std::istream_iterator<int>(), std::back_inserter(data));
  
    // 使用 ostream_iterator 输出数据到标准输出
    std::cout << "You entered: ";
    std::copy(data.begin(), data.end(), std::ostream_iterator<int>(std::cout, " "));
    std::cout << std::endl;
  
    return 0;
  }
  ```
- 在这个示例中，我们使用 `std::istream_iterator` 从标准输入读取整数，直到达到文件结束标记（EOF）。然后，使用 `std::ostream_iterator` 将读入的数据输出到标准输出。
- ### 注意事项
	- 使用单通迭代器时，需要特别注意不要尝试重新访问或修改已经通过迭代器访问过的元素，这可能导致未定义行为。
	- 单通迭代器非常适合流式处理和管道操作，其中数据一次生成并消费，而不需要存储整个数据集。
- 单通迭代器提供了一种在 C++ 中进行序列化输入和输出操作的灵活方法，尤其适合处理大数据流或者在资源受限的环境中进行数据处理。
  <!--Converted by ToLogseq-->