alias:: constexpr

- #C++keyword #C++11
- `constexpr` 修饰符用来声明可以在[[编译]]时计算函数或变量的值。指明了变量或函数的值 可以用在 只允许出现[[常量表达式]]的地方。
  id:: 652d4d17-8c8f-40e1-a702-1e77b3ae8f66
- 在函数或[[static]]数据成员（自[[C++17]]起）声明中使用 `constexpr` 修饰符意味着[[inline]]。
- ## [[constexpr variable]]
  constexpr 变量必须满足以下要求：
	- 其类型必须是[[LiteralType]]。
	- 必须 立即初始化。
	- 其初始化的[[完整表达式]]，包括所有[[隐式转换]]、[[构造函数]]调用等，必须是[[常量表达式]]。
	- 必须具有[[constant destruction]]（自[[C++20]]起）。
- [[constexpr function]]
	-