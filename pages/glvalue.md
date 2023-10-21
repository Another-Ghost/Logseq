alias:: generalized lvalue

- glvalue 是一个表达式，可以是[[lvalue]]或[[xvalue]]。
- # 特性
	- glvalue 可以通过[[lvalue-to-rvalue]]、[[array-to-pointer]]或[[function-to-pointer]]的[[隐式转换]]成[[prvalue]]。
	  logseq.order-list-type:: number
	- glvalue 可能是[[多态]]的：它所标识的对象的[[动态类型]]不一定是表达式的[[静态类型]]。
	  logseq.order-list-type:: number
	- glvalue 可以具有[[incomplete type]]，只要表达式允许。
	  logseq.order-list-type:: number
-