- `static_cast` 能够执行指针之间的转换，不仅限于 [[upcast]] ，还包括[[downcast]]。在运行时**不会执行检查**以确保被转换的对象实际上是目标类型的完整对象。因此，由程序员来确保转换是安全的。
  另一方面，它不会引入像 `dynamic_cast` 那样的类型安全检查的开销。
- ```cpp
  class Base {};
  class Derived: public Base {};
  Base * a = new Base;
  Derived * b = static_cast<Derived*>(a);
  ```
- 这是有效的代码，尽管`b`会指向一个类的不完整对象，如果进行解引用操作可能导致运行时错误。
  id:: 65329f33-5c23-466a-a31f-d46513f820b7
- `static_cast`能够执行所有**允许的**[[隐式转换]]（不仅是与类的指针相关的转换），并且也能执行这些转换的相反操作。它可以：
  id:: 65329f33-a58e-42c7-83b9-0b47506a2821
	- 从 `void*` 转换为任何指针类型。在这种情况下，它保证如果`void*`值是通过从**相同的指针类型**进行转换而获得的，那么结果指针值是相同的。
	  logseq.order-list-type:: number
	- 将整数、浮点值和枚举类型转换为[[枚举类型]]。
	  logseq.order-list-type:: number
	  id:: 65329f33-7d94-4288-96d1-271a2235ae28
- 此外，`static_cast` 还能执行以下操作：
	- 显式调用[[单参数构造函数]]或[[conversion 运算符]]。
	  logseq.order-list-type:: number
	- 转换为[[右值引用]]。
	  logseq.order-list-type:: number
	- 将[[枚举类]]的值转换为整型或浮点值。
	  logseq.order-list-type:: number
	- 将任何类型转换为`void`，并[[求解]]和[[丢弃]]该值。
	  logseq.order-list-type:: number