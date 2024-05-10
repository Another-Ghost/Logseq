alias:: 链接, 链接性

- # C++中的链接
	- 一个表示 对象、引用、函数、类型、模板、命名空间 或 值 的[[名称]]可能具有[[链接]]。
	  如果一个[[名称]]具有链接，它与 在另一个[[作用域]]中声明的相同名称 具有同一个[[实体]]。
	  如果在多个[[作用域]]中声明了具有 相同名称 的变量、函数或其他实体，但没有链接，那么将生成多个[[实体]]的[[实例]]。
	- # 链接类型：
		- ## [[no linkage]]
			- 该名称只能从其所在的作用域引用。
				- 在**[[块作用域]]**声明的以下名称没有链接性：
					- 没有明确声明为 extern 的变量（无论 static 修饰符如何）；
					  logseq.order-list-type:: number
					- 局部类及其成员函数；
					  logseq.order-list-type:: number
					- 在块作用域声明的其他名称，如 typedef、枚举和枚举器。
					  logseq.order-list-type:: number
				- 没有指定[[外部链接]]、[[模块链接]]（自[[C++20]]起）或[[内部链接]]的名称，**无论它们在哪个作用域中声明**，也没有链接。
		- ## [[internal linkage]]
			- 该名称可以从当前[[translation unit]]的所有[[作用域]]引用。
			- 在[[命名空间作用域]]声明的以下名称具有 内部链接 ：
				- 声明为[[static]]的变量、变量模板（自[[C++14]]起）、函数或函数模板；
				  logseq.order-list-type:: number
				- 非模板的（自[[C++14]]起）非[[cv-修饰符]] 限定类型的 变量，除非
				  logseq.order-list-type:: number
					- 它们是[[内联]]的（自[[C++17]]起）；
					  logseq.order-list-type:: number
					- 它们在[[module interface unit]]的范围内声明（如果有的话）或模块分区之外；
					  logseq.order-list-type:: number
					- 它们被显式声明为 extern；
					  logseq.order-list-type:: number
					- 它们之前被声明过，先前的声明没有 内部链接；
					  logseq.order-list-type:: number
				- [[匿名 union]]的数据成员。
				  logseq.order-list-type:: number
			- 此外，所有在**未命名**的命名空间 或 未命名命名空间中的命名空间 中声明的名称，即使明确声明为[[extern]]，也具有内部链接性。
		- ## [[external linkage]]
- # [[静态链接]]
- # [[动态链接]]
-