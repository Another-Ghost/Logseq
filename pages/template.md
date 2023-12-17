alias:: 模板

- 在 C++ 编程语言中，[[模板]]是一种[[实体]]，用于定义以下一种或多种结构：
	- 类[[family]]（[[class template]]），这可能包括[[嵌套类]]（nested class）。
	  logseq.order-list-type:: number
	- 函数 family（[[function template]]），这可能包括[[成员函数]]。
	  logseq.order-list-type:: number
	- 类型 family 的别名（[[alias template]]）。
	  logseq.order-list-type:: number
	- 变量 family（[[variable template]]）([[C++14]])。
	  logseq.order-list-type:: number
	- [[concept]]。
	  logseq.order-list-type:: number
- [[模板]]通过一个或多个[[模板参数]]（template parameter）来[[参数化]]，这些参数分为三种类型：[[类型模板参数]]（type template parameter）、[[非类型模板参数]]（non-type template parameter）和[[模板模板参数]]（template template parameter）。
- 当提供 模板参数 时，或者对于[[函数模板]]和 [[类模板]]（自[[C++17]]起），[[模板参数]]**可以被推导出来**，它们被用来替换模板参数，从而得到模板的[[特化]]（specialization），即一个特定类型或一个特定函数[[左值]]。
	- [[模板特化]]也可以显式提供：允许[[类模板]]、[[变量]]和[[函数模板]][[完全特化]]，
	- 而只允许[[类模板]]和[[变量模板]][[部分特化]]。
- 当 引用[[类模板特化]]时，如果上下文要求一个[[完整对象类型]]，或者当 引用[[函数模板特化]]时，如果上下文要求存在一个[[函数定义]]，那么模板就会被[[实例化]]（即代码实际上会被[[编译]]），**除非**该模板已经[[显式特化]]或[[显式实例化]]。
  [[类模板]]的[[实例化]]**不会**[[实例化]]其任何[[成员函数]]，**除非这些成员函数也被使用**。
  在[[链接]]时，由不同[[翻译单元]]生成的**相同[[实例化]]将会合并**。
- [[类模板定义]]必须在[[隐式实例化]]的点可见，这就是为什么[[模板库]]通常在[[头文件]]中提供所有[[模板定义]]的原因（例如，大多数 Boost 库都是[[仅头文件]]的）。
- # 语法
	- ``` 
	  template <parameter-list> requires-clause(optional) declaration
	  `template <parameter-list> concept concept-name = constraint-expression; //C++20
	  ```
		- `parameter-list` 是一个非空的逗号分隔列表，包含[[模板参数]]，每个参数可以是非类型参数、类型参数、模板参数，或者是任何这些的[[参数包]]。
		- `requires-clause`（自[[C++20]]起）是一个指定模板参数[[约束]]的[[requires-clause]]。
- # [[template-id]]
	- ```
	  template-name <parameter-list>		
	  ```
		- `template-name` 可以是：
			- 命名模板的标识符（这称为[[simple-template-id]]）。
			  logseq.order-list-type:: number
			- [[重载操作符模板]]。
			  logseq.order-list-type:: number
			- 用户定义的[[literal template]]的名称。
			  logseq.order-list-type:: number
			  <<<<<<< HEAD
- # [[templated entity]]