alias:: move-eligible expressions, move-eligible

- 尽管包含任何[[变量名称]]的表达式都是[[lvalue]]表达式，但如果它作为以下 *操作符* 的 *运算元* 之一，该表达式可能是“可移动的”（[[move-eligible]]）：
	- 返回语句（[[return]]）
	  logseq.order-list-type:: number
	- 协程返回语句（[[co_return]]，自[[C++20]]起）
	  logseq.order-list-type:: number
	- 异常抛出表达式（[[throw]]，自[[C++17]]起）
	  logseq.order-list-type:: number
- >如果一个表达式是[[move-eligible]]，它在[[overload resolution]]的目的上被视为右值（自[[C++23]]起），这意味着它可能选择[[移动构造函数]]。有关详细信息，请参阅[Automatic move from local variables and parameters](https://en.cppreference.com/w/cpp/language/return#Automatic_move_from_local_variables_and_parameters) 。
-