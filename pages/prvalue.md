alias:: pure rvalue

- 属于 `prvalue` 的表达式如下：
  id:: 65340fa8-3eb9-4bc8-900e-e6cbd3b9e347
	- [[literals]]（不包括字符串字面值），比如 `42`、`true` 或 `nullptr`。
	  logseq.order-list-type:: number
- 函数调用或重载运算符表达式，其返回类型是非引用类型，比如 `str.substr(1, 2)`、`str1 + str2` 或 `it++`。
- 内置的后增和后减表达式，即 `a++` 和 `a--`。
- 所有其他内置算术表达式，如 `a + b`、`a % b`、`a & b`、`a << b` 等。
- 内置的逻辑表达式，包括 `a && b`、`a || b`、`!a` 等。
- 内置的比较表达式，包括 `a < b`、`a == b`、`a >= b` 等。
- 内置的取地址表达式，即 `&a`。
- 对象成员表达式 `a.m`，其中 `m` 是成员枚举器或非静态成员函数。
- 指针成员表达式 `p->m`，其中 `m` 是成员枚举器或非静态成员函数。
- 对象的指针成员表达式 `a.*mp`，其中 `mp` 是成员函数的指针。
- 指针的指针成员表达式 `p->*mp`，其中 `mp` 是成员函数的指针。
- 内置的逗号表达式，其中 `b` 是 `prvalue`。
- 三元条件表达式 `a ? b : c`，对于特定的 `b` 和 `c`（具体定义详见标准文档）。
- 强制类型转换表达式为非引用类型，比如 `static_cast<double>(x)`、`std::string{}` 或 `(int)42`。
- `this` 指针。
- 枚举器（enumerator）。
- 标量类型的非类型模板参数。
- Lambda 表达式，比如 `[](int x){ return x * x; }`（自 C++11 起）。
- `requires` 表达式，比如 `requires (T i) { typename T::type; }`。
- 概念的特化，比如 `std::equality_comparable<int>`（自 C++20 起）。