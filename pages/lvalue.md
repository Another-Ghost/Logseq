alias:: lvalues, 左值

- 一个[[lvalue]]（因为在历史上，[[lvalues]]可以出现在[[赋值表达式]]的左侧而得名）是一个不是[[xvalue]]的[[glvalue]]。
- 属于 lvalue 的表达式如下：
	- 变量、函数、[[template parameter object]]（自[[C++20]]起）或数据成员的[[name]]，无论类型如何，比如 `std::cin` 或 `std::endl`。即使变量的类型是[[右值引用]]，其[[名称]]**组成的表达式**仍然是 `lvalue` 表达式（参见[[move-eligible expression]]）。
	  logseq.order-list-type:: number
	  >例如：`std::move{a}`是[[右值引用]]，但`std::move{a}.m`仍然是左值。
	  这里的[[name]]相当于[[identity]]，是一种标识，包括变量名，函数名，成员变量名。
	- *函数调用* 或 *重载运算符* 表达式，其[[返回类型]]为[[左值引用]]，例如`std::getline(std::cin, str)`、`std::cout << 1`、`str1 = str2` 或 `++it`。
	  logseq.order-list-type:: number
	- `a = b`、`a += b`、`a %= b` 以及所有其他 *内置赋值* 和 *复合赋值表达式* 。
	  logseq.order-list-type:: number
	- `++a` 和 `--a`，内置的前增和前减表达式。
	  logseq.order-list-type:: number
	- `*p`，内置的[[indirection]]表达式。
	  logseq.order-list-type:: number
	- `a[n]` 和 `p[n]`，内置的[[下标]]表达式，其中 `a[n]` 中的一个 *操作数* 是数组的左值。
	  logseq.order-list-type:: number
	- *对象成员* 表达式 `a.m`，除非 `m` 是 *成员枚举器* 或 *非静态成员函数* ，或者 `a` 是[[右值]]且 `m` 是对象类型的 *非静态数据成员* 。
	  logseq.order-list-type:: number
	- *指针成员* 表达式 `p->m`，除非 `m` 是 *成员枚举器* 或 *非静态成员函数* 。
	  logseq.order-list-type:: number
	- *对象的指针成员* 表达式 `a.*mp`，其中 `a` 是 *左值* ，`mp` 是数据成员的指针。
	  logseq.order-list-type:: number
	- 指针的指针成员表达式 `p->*mp`，其中 `mp` 是数据成员的指针。
	  logseq.order-list-type:: number
	- *内置逗号* 表达式 `a, b`，其中 `b` 是左值。
	  logseq.order-list-type:: number
	- 对于特定的 `b` 和 `c`的 *三元条件* 表达式 `a ? b : c`（例如，当它们都是相同类型的 *左值* 时，但具体定义见[definition](https://en.cppreference.com/w/cpp/language/operator_other#Conditional_operator)）。
	  logseq.order-list-type:: number
	- [[string literals]]，比如 `"Hello, world!"`。
	  logseq.order-list-type:: number
	- [[类型转换]]表达式为 *左值引用* 类型，例如 `static_cast<int&>(x)` 或 `static_cast<void(&)(int)>(x)`。
	  logseq.order-list-type:: number
	- 左值引用类型的**非类型**[[模板参数]]。
	  logseq.order-list-type:: number
	- *函数调用* 或 *重载运算符* 表达式，其[[返回类型]]为**函数**的[[右值引用]]。
	  logseq.order-list-type:: number
	- [[类型转换]]表达式为[[函数类型]]的[[右值引用]]，例如 `static_cast<void(&&)(int)>(x)`。
	  logseq.order-list-type:: number
- # 特性
	- 与 `glvalue`（通用左值）相同的属性。
	  logseq.order-list-type:: number
	- 可以通过内置的[[取地址操作符]] `&` 取一个 `lvalue` 的[[地址]]。例如，`&++i[1]` 和 `&std::endl` 都是有效的表达式。
	  logseq.order-list-type:: number
	- *可修改的* `lvalue` 可以作为内置的[[赋值]]和 *复合赋值操作符* 的 *左操作数* 。
	  logseq.order-list-type:: number
	- `lvalue` 可以用来初始化[[左值引用]]；这将使新名称与表达式所标识的对象关联起来。
	  logseq.order-list-type:: number
-