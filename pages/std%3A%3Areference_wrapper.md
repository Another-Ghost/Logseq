- #<functional>
- `std::reference_wrapper` 是 C++11 引入的一个模板类，位于 `<functional>` 头文件中。它是对引用的包装，提供了一种将引用作为对象存储和传递的方式，同时保留了对原始对象的引用语义。由于**直接的[[引用]]不能作为对象存在（比如存储在[[容器]]中或作为[[函数返回值]]）**，`std::reference_wrapper` 提供了一种灵活的解决方案。
- ### 主要特性和用法
- **可复制**：`std::reference_wrapper` 是可复制的。复制 `std::reference_wrapper` 对象不会复制它所引用的对象，而是创建一个新的引用包装器，指向同一个对象。
- **可赋值**：可以将一个 `std::reference_wrapper` 对象赋值给另一个，赋值操作会更改引用的目标，使之指向新的对象。
- **支持隐式转换**：`std::reference_wrapper` 支持隐式转换回被引用的类型，这意味着你可以在期望原始类型的地方使用它。
- **获取被引用对象**：通过调用 `get()` 成员函数，可以获取被引用对象的引用。
- **用于标准库算法和容器**：特别适用于标准库算法和容器，允许将引用存储在标准容器中，或者将引用作为算法的参数传递。
- ### 示例
  
  以下是 `std::reference_wrapper` 的一个简单示例，展示如何在容器中存储引用：
  
  ```cpp
  #include <iostream>
  #include <vector>
  #include <functional> // 包含 std::reference_wrapper
  
  int main() {
    int a = 10, b = 20, c = 30;
    // 创建一个包含引用的 vector
    std::vector<std::reference_wrapper<int>> vec = {a, b, c};
  
    // 修改引用的目标
    for(auto& ref : vec) {
        ref.get() += 5; // 使用 get() 访问并修改被引用的对象
    }
  
    // 输出原始变量的值来证明它们被修改了
    std::cout << "a = " << a << ", b = " << b << ", c = " << c << std::endl;
  
    return 0;
  }
  ```
  
  在这个示例中，`vec` 是一个包含 `int` 引用的 `vector`。通过修改 `vec` 中的引用，原始变量 `a`、`b`、`c` 的值也相应被修改了，这说明存储在容器中的是对原始变量的引用而非副本。
- ### 注意事项
- 被 `std::reference_wrapper` 引用的对象必须在引用包装器使用期间保持有效。如果原始对象被销毁，通过 `std::reference_wrapper` 访问它将导致未定义行为。
- 由于 `std::reference_wrapper` 实质上包含了引用，因此不能将其用于引用不存在的对象，比如临时对象。
- `std::reference_wrapper` 对于标准库函数特别有用，因为许多标准库函数要求传递的对象是可复制的，而普通引用不能满足这一要求。
  
  `std::reference_wrapper` 提供了一种在C++中**以值语义传递引用**的灵活方式，使得引用可以更加灵活地用于各种场合，包括存储在容器中或作为函数参数。