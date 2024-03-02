alias:: memcpy

- `memcpy` 是 C 和 C++ 标准库中的一个函数，用于从源内存地址复制 n 个字节到目标内存地址。它是定义在 `<cstring>`（在 C 中是 `<string.h>`）头文件中的一个非常基础且高效的内存操作函数。
- ### 函数原型
  
  ```cpp
  void* memcpy(void* dest, const void* src, size_t n);
  ```
	- **`dest`**：指向用于存储复制内容的目标内存地址的指针。
	- **`src`**：指向要复制的源内存地址的指针。
	- **`n`**：要复制的字节数。
- ### 返回值
  
  `memcpy` 返回一个指向目标内存地址（`dest`）的指针。
- ### 使用注意事项
	- **重叠内存**：如果源（`src`）和目标（`dest`）内存区域重叠，`memcpy` 的行为是未定义的。对于重叠内存区域的复制，应使用 `memmove` 函数。
	- **类型安全**：由于 `memcpy` 使用 `void*` 类型的指针，它不进行类型检查，因此使用时需要确保正确地处理数据类型和大小。
	- **性能**：`memcpy` 通常是高度优化的，能够利用特定硬件的优势来实现快速的内存复制，尤其是对于大块内存的操作。
- ### 示例
  
  ```cpp
  #include <iostream>
  #include <cstring>
  
  int main() {
    char src[] = "Hello, World!";
    char dest[50];  // 确保有足够的空间
  
    memcpy(dest, src, strlen(src) + 1);  // 加1以包含终止符'\0'
  
    std::cout << "Copied string: " << dest << std::endl;
  
    return 0;
  }
  ```
  
  在这个示例中，`memcpy` 将字符串从 `src` 复制到 `dest`，包括字符串的终止符 `'\0'`。
- ### 总结
  
  `memcpy` 是处理底层内存操作时的有力工具，适用于需要快速复制大量数据的场景。然而，正确使用它需要注意目标和源内存区域的重叠问题，以及保持类型安全。对于需要类型安全或更高级别抽象的情况，C++ 提供了标准库容器和算法，如[[std::copy]]，它们可能是更好的选择。