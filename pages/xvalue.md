alias:: eXpiring value

- `xvalue` 表达式的特点如下：
	- 对象成员表达式 `a.m`，其中 `a` 是[[右值]]，`m` 是对象类型的 *非静态数据成员* 。
	  logseq.order-list-type:: number
	- 对象表达式的成员指针 `a.*mp`，其中 `a` 是[[右值]]，`mp` 是指向数据成员的指针。
	  logseq.order-list-type:: number
	  id:: 6533be27-f68d-438b-adf2-6b8681eddc02
	- 内置逗号表达式 `a, b`，其中 `b` 是 `xvalue`。
	  logseq.order-list-type:: number
	- [[三元条件表达式]] `a ? b : c`，对于特定的 `b` 和 `c`，其中 `b` 和 `c` 都是 `xvalue`。
	  logseq.order-list-type:: number
	- [[函数调用]]或[[重载运算符]]表达式，其[[返回类型]]为对象的[[右值引用]]，例如 `std::move(x)`。
	  logseq.order-list-type:: number
	- 内置[[下标]]表达式 `a[n]`，其中一个[[运算元]]是数组右值（自[[C++11]]起）。
	  logseq.order-list-type:: number
	- [[类型转换]]表达式为对象类型的右值引用，例如 `static_cast<char&&>(x)`（自[[C++11]]起）。
	  logseq.order-list-type:: number
	- 任何指代[[临时对象]]的表达式，在[[temporary materialization]]后（自[[C++17]]起）。
	  logseq.order-list-type:: number
	- [[move-eligible expressions]] （自[[C++23]]起）。
	  logseq.order-list-type:: number
- [[xvalue]]具有与[[rvalue]]相同的特性，同时也具有与[[glvalue]]相同的特性。
- 特别地，像所有的右值一样，`xvalue` 绑定到右值引用，像所有的左值一样，`xvalue` 可能是[[多态]]的，而且非[[类]]类型的 `xvalue` 可能带有[[cv 限定符]]。