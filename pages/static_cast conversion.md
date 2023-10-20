- `static_cast` 是一个 C++ 中用于进行类型转换的操作符，它结合了[[隐式转换]]和用户定义的转换。
- # 语法
	- ``` C++
	  static_cast<target-type>(expression)
	  ```
	  返回一个类型为 *target-type* 的值.
- # 解释
	- 只有在这些情况下可以使用 `static_cast` 进行转换，但不包括这些转换会去除`const`或`volatile`修饰的情况：
		- 如果 *target-type* 是某个[[类]] D 的[[引用]]，而 *expression* 是其non-[[virtual base class]] B 的[[lvalue]]，或者 *target-type* 是某个完整类 D 的指针，而表达式是其非虚基类 B 的[[prvalue]]指针，`static_cast` 执行一[[downcast]]。
		  logseq.order-list-type:: number
		  id:: 65325f02-b5eb-49dc-a66a-40ec8f0ee0e5
		  如果 B 是 D 的模糊、不可访问或虚基类（或虚基类的基类），这种 downcast 是非法的。
		  这种 downcast 不会在运行时检查对象的运行时类型是否确实为 D ，只有在其他方式（例如实现[[静态多态性]]时）可以保证这个前提条件的情况下才能安全使用。
		  安全的 downcast 可以使用[[dynamic_cast]]完成。
		-
-