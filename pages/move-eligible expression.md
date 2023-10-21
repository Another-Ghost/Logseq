alias:: move-eligible expressions

- 尽管包含任何[[变量名称]]的表达式都是[[lvalue]]表达式，但如果它作为以下 *操作符* 的 *运算元* 之一，该表达式可能是“可移动的”（move-eligible）：
	- 返回语句（[[return]]）
	  logseq.order-list-type:: number
	- 协程返回语句（[[co_return]]，自[[C++20]]起）
	  logseq.order-list-type:: number
	- 异常抛出表达式（[[throw]]，自[[C++17]]起）
	  logseq.order-list-type:: number
- 如果一个表达式是可移动的，它在重载决议的目的上被视为右值（自 C++23 起）或左值（C++23 之前），这意味着它可能选择移动构造函数。有关详细信息，请参阅有关从本地变量和参数自动移动的内容。