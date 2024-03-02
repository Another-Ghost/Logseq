alias:: memcmp()

- `memcmp` 是一个来自 C 标准库（在 `<cstring>` 或 `<string.h>` 中定义）的函数，用于比较两块内存区域。这个函数对于判断两个非类型化的内存块是否相等非常有用，特别是当你处理的数据不是以标准C++容器或对象形式存在时。
- ### 函数原型
  
  ```c
  int memcmp(const void* ptr1, const void* ptr2, size_t num);
  ```
	- **`ptr1`**：指向第一块要比较的内存的指针。
	- **`ptr2`**：指向第二块要比较的内存的指针。
	- **`num`**：要比较的字节数。
- ### 返回值
	- **返回 < 0**：如果在 `num` 字节内 `ptr1` 所指的内存块小于 `ptr2` 所指的内存块。
	- **返回 0**：如果在 `num` 字节内两个内存块完全相同。
	- **返回 > 0**：如果在 `num` 字节内 `ptr1` 所指的内存块大于 `ptr2` 所指的内存块。
	- 比较是基于[[无符号字符]]的，即使你比较的是其他类型的数据，比较也是按[[字节]]进行，从两块内存的开始位置开始，直到达到指定的 `num` 字节数或找到不相等的字节。
- ### 示例用法
  
  ```c
  #include <cstring>
  #include <iostream>
  
  int main() {
    char array1[] = "Hello, World!";
    char array2[] = "Hello, World!";
  
    // 比较两个字符串的前 5 个字符
    if (memcmp(array1, array2, 5) == 0) {
        std::cout << "First 5 characters are equal." << std::endl;
    } else {
        std::cout << "First 5 characters are not equal." << std::endl;
    }
  
    return 0;
  }
  ```
- ### 使用注意事项
	- `memcmp` 对于比较简单的数据类型或者结构体非常有效，但对于包含[[动态内存指针]]或需要深度比较的复杂数据结构，可能不适用。
	- 当使用 `memcmp` 比较两个对象时，需要确保这种比较对于所涉及的数据类型是安全的。对于有些类类型，直接比较内存可能会忽略[[类的比较语义]]或导致未定义行为。
	- 由于 `memcmp` 是基于字节的比较，它不考虑数据的实际类型，因此可能会因为字节表示的差异（如[[字节序]]）而导致意外的比较结果。
-