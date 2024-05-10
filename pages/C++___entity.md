alias:: C++/实体

- [[C++程序]]的[entity]([[C++/entity]])包括[[值]]、[[对象]]、[[引用]]、[[structured binding]]、[[函数]]、[[枚举器]]、[[类型]]、[[类成员]]、[[模板]]、[[模板特化]]、[[参数包]]和[[命名空间]]。
  #+BEGIN_NOTE
  [[预处理器宏]]不是[[C++ entity]]。
  #+END_NOTE
- 实体的特性
	- [[链接]]：实体可以具有外部链接、内部链接或无链接。外部链接允许实体在多个翻译单元中共享。
	  logseq.order-list-type:: number
	- [[作用域]]：实体的作用域决定了它在代码中的可见性。作用域包括局部、类、命名空间等。
	  logseq.order-list-type:: number
	- [[生命周期]]：实体的生命周期决定了它在程序中的持续时间。从短暂的局部变量到贯穿整个程序的全局变量。
	  logseq.order-list-type:: number
	- [[可访问性]]：类的成员变量和成员函数的可访问性可以是公有、私有或保护。
	  logseq.order-list-type:: number