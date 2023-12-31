alias:: noexcept

- #C++Keyword
- `noexcept`运算符执行一个在**编译时**进行的检查，如果一个[[C++ 表达式]]声明为不会引发任何[[异常]]，则返回 `true`。
- 它可以在[[函数模板]]的`noexcept specifier`内使用，以声明该函数对**某些类型**会引发[[异常]]，但对其他类型不会引发异常。
- ``` C++
  noexcept(expression)
  ```
- ## 解释
- `noexcept`运算符不会对[[C++ 表达式]]进行求值。
- 在[[C++17]]之前如果表达式的[[潜在异常】】集为空，其结果为`true`；
  而在[[C++17]]之后，如果表达式为[[non-throwing]]，则结果为`true`，否则为`false`。
- https://en.cppreference.com/w/cpp/language/noexcept