alias:: 内联, inline specifier

- [[内联函数]]
- [[内联变量]]
- 内联函数或内联变量（自 C++17 起）具有以下特性：
	- 内联函数或变量的定义（自 C++17 起）必须在访问它的翻译单元中可达（不一定在访问点之前）。
	  logseq.order-list-type:: number
	- 具有外部链接的内联函数或变量（例如，未声明为 static）具有以下额外特性：
	  logseq.order-list-type:: number
		- 程序中可以有多个内联函数或变量的定义（自 C++17 起），只要每个定义出现在不同的翻译单元中，且（对于非静态的内联函数和变量）所有定义都相同。例如，一个内联函数或内联变量可以定义在一个头文件中，该头文件被多个源文件包含。
		  logseq.order-list-type:: number
		- 它必须在每个翻译单元中声明为内联。
		  logseq.order-list-type:: number
		- 它在每个翻译单元中具有相同的地址。
		  logseq.order-list-type:: number
- 在内联函数中：
	- 所有函数定义中的函数局部静态对象在所有翻译单元中共享（它们都引用同一个翻译单元中定义的同一个对象）。
	- 所有函数定义中定义的类型在所有翻译单元中也是相同的。
- inline 关键字最初的意图是作为优化器的指示符，表明优先进行函数的内联替换而不是函数调用，即，不执行函数调用 CPU 指令来转移控制到函数体，而是执行函数体的副本而不生成调用。这避免了函数调用创建的开销（传递参数和获取结果），但可能导致可执行文件变大，因为函数的代码必须多次重复。
- 由于 inline 关键字对函数的这种含义是非强制性的，编译器可以对任何未标记为 inline 的函数使用内联替换，也可以对任何标记为 inline 的函数生成函数调用。这些优化选择不改变上述关于多重定义和共享静态变量的规则。
- 由于 inline 关键字对函数的含义变成了“允许多个定义”而不是“优先进行内联”，这种含义被扩展到了变量上。