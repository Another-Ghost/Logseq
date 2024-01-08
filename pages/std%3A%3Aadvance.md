- `std::advance` 是 C++ 标准库中的一个函数，它用于改变迭代器的位置。它是 `<iterator>` 头文件的一部分。这个函数接受一个迭代器和一个距离值作为参数，并将迭代器向前或向后移动指定的距离。`std::advance` 可以用于任何类型的迭代器，包括随机访问迭代器、双向迭代器和前向迭代器。
- ### 使用方式
  
  ```cpp
  std::advance(iterator, distance);
  ```
- `iterator`：要改变位置的迭代器。
- `distance`：一个整数，表示移动的元素数。如果 `distance` 为正数，则迭代器向前移动；如果为负数，迭代器向后移动（只适用于双向和随机访问迭代器）。
- ### 示例
  
  ```cpp
  #include <iostream>
  #include <vector>
  #include <list>
  #include <iterator>
  
  int main() {
    std::vector<int> vec = {10, 20, 30, 40, 50};
    auto vec_it = vec.begin();
    std::advance(vec_it, 2);  // 移动到第三个元素
    std::cout << "The third element in vector is: " << *vec_it << std::endl;
  
    std::list<int> lst = {10, 20, 30, 40, 50};
    auto lst_it = lst.begin();
    std::advance(lst_it, 3);  // 移动到第四个元素
    std::cout << "The fourth element in list is: " << *lst_it << std::endl;
  
    return 0;
  }
  ```
  
  在这个示例中，`std::advance` 用于在一个 `std::vector` 和一个 `std::list` 中移动迭代器。
- ### 性能
- 对于**随机访问迭代器**（如 `std::vector` 和 `std::deque` 的迭代器），`std::advance` 的效率非常高，时间复杂度为 O(1)。
- 对于**双向迭代器**（如 `std::list` 的迭代器）和**前向迭代器**，`std::advance` 通过线性移动来改变迭代器的位置，时间复杂度为 O(n)。
- ### 注意事项
- 确保在移动迭代器时不会超出容器的范围。
- 当使用负数作为距离参数时，确保迭代器类型支持向后移动（例如，双向或随机访问迭代器）。前向迭代器不支持负数距离。