- #C++keyword
- 声明为^^mutable^^的类成员允许被修改，即使包含这个类成员的对象被声明为 ``const`` 。
- 关键字^^mutable^^在 C++ 语言语法中是[[存储类别说明符]]，尽管它不影响 存储期 或 链接 。
- `mutable`可以在非[[static]] 类成员 的非[[引用]]非[[const]]类型的声明中出现：
  ```C++
  class X
  {
      mutable const int* p; // 可行（底层 const, p 本身类型不是 const, p 所指的对象类型为 const）
      mutable int* const q; // 非法
      mutable int& r;      // 非法
  };
  ```