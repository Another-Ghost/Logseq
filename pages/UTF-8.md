alias:: 8-bit Unicode Transformation Format

- [[UTF-8]]（**）是一种针对[[Unicode]]的 *可变长度* 的[字符编码]，也是一种[[前缀码]]。它可以用一至四个字节对[[Unicode]]字符集中的所有有效[[编码点]]进行编码。
- 由于较小值的编码点一般使用频率较高，直接使用Unicode编码效率低下，大量浪费内存空间。UTF-8 就是为了解决向后兼容 ASCII码而设计，Unicode中前128个字符，使用与[[ASCII码]]相同的二进制值的 单个字节 进行编码，而且字面与ASCII码的字面一一对应。
-