alias:: pure rvalue

- 属于 `prvalue` 的表达式如下：
  id:: 65340fa8-3eb9-4bc8-900e-e6cbd3b9e347
	- [[literals]]（不包括字符串字面值），比如 `42`、`true` 或 `nullptr`。
	  logseq.order-list-type:: number
	- *函数调用* 或 *重载运算符* 表达式，其返回类型是 *非引用类型*，比如 `str.substr(1, 2)`、`str1 + str2` 或 `it++`。
	  logseq.order-list-type:: number
	- 内置的后增和后减表达式，即 `a++` 和 `a--`。
	  logseq.order-list-type:: number
	- 所有其他内置 *算术表达式*，如 `a + b`、`a % b`、`a & b`、`a << b` 等。
	  logseq.order-list-type:: number
	- 内置的 *逻辑表达式* ，包括 `a && b`、`a || b`、`!a` 等。
	  logseq.order-list-type:: number
	- 内置的 *比较表达式* ，包括 `a < b`、`a == b`、`a >= b` 等。
	  logseq.order-list-type:: number
	- 内置的[[取地址]]表达式，即 `&a`。
	  logseq.order-list-type:: number
	- *对象成员* 表达式 `a.m`，其中 `m` 是 *成员枚举器* 或 *非静态成员函数* 。
	  logseq.order-list-type:: number
	- *指针成员* 表达式 `p->m`，其中 `m` 是 *成员枚举器* 或 *非静态成员函数* 。
	  logseq.order-list-type:: number
	- *对象的指针成员* 表达式 `a.*mp`，其中 `mp` 是 *成员函数* 的指针。
	  logseq.order-list-type:: number
	- *指针的指针成员* 表达式 `p->*mp`，其中 `mp` 是 *成员函数* 的指针。
	  logseq.order-list-type:: number
	- 内置的[[逗号]]表达式 `a, b`，其中 `b` 是 `prvalue`。
	  logseq.order-list-type:: number
	- *三元条件表达式* `a ? b : c`，对于特定的 `b` 和 `c`（具体定义见[definition](https://en.cppreference.com/w/cpp/language/operator_other#Conditional_operator)）。
	  logseq.order-list-type:: number
	- [[类型转换]]表达式为 *非引用类型* ，比如 `static_cast<double>(x)`、`std::string{}` 或 `(int)42`。
	  logseq.order-list-type:: number
	- [[this]]指针。
	  logseq.order-list-type:: number
	- [[枚举值]]。
	  logseq.order-list-type:: number
	- *标量类型* 的非类型[[模板参数]]。
	  logseq.order-list-type:: number
	- [[Lambda 表达式]]，比如 `[](int x){ return x * x; }`。
	  logseq.order-list-type:: number
	- [[requires-expression]]，比如 `requires (T i) { typename T::type; }`（自[[C++20]] 起）。
	  logseq.order-list-type:: number
	- [[concept]]的特化，比如 `std::equality_comparable<int>`（自[[C++20]]起）。
	  logseq.order-list-type:: number
- 特性：
	- 与[[rvalue]]相同。
	  logseq.order-list-type:: number
	- prvalue 不能是[[多态]]的：它表示的对象的[[动态类型]]始终是 *表达式的类型* 。
	  logseq.order-list-type:: number
	  id:: 6534333b-f974-4cc9-bd5c-8089f1c27a4b
	- 非[[类]]非[[数组]]的 prvalue 通常不能具有[[cv 限定符]]，除非它被[[materialized]]以绑定到[[cv 限定符]]类型的引用（自[[C++17]]起）。 
	  logseq.order-list-type:: number
	  >注意：函数调用或类型转换表达式可能会导致非类 cv 限定符类型的 prvalue，但通常会立即删除 cv 限定符。
	- prvalue 不能具有[[incomplete type]]（除了[[void]]类型，或在 [[decltype]]说明符中使用时）。
	  logseq.order-list-type:: number
	- prvalue 不能具有[[抽象类]]类型或其 *数组* 。
	  logseq.order-list-type:: number
-