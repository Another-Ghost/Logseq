alias:: 常量表达式

- 可以在[[编译期]][[求值]]的[[表达式]]称为[[常量表达式]]。
- 这类表达式可以用作 非类模板参数、数组大小 以及其他需要[[常量表达式]]的上下文中，例如：
  #+BEGIN_PINNED
  ```cpp
  int n = 1;
  std::array<int, n> a1;  // 错误：n 不是常量表达式
  const int cn = 2;
  std::array<int, cn> a2; // 正确：cn 是常量表达式
  ```
  #+END_PINNED