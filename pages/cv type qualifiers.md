alias:: cv-qualifiers, cv-修饰符, cv-qualification, cv 限定符

- #C++Keyword
- ## `const`和 `volatile`类型修饰符
	- [[const]] 和 [[volatile]] [[类型修饰符]]出现在任何[[类型说明符]]中，包括声明语法，以指定正在声明的对象或正在命名的类型的constness（常量性）或volatility（易变性）。
	- ## 解释
		- 任何类型，除了[[函数]]类型或[[引用]]类型，都属于以下四种不同但相关的类型之一：
			- 无 cv 修饰版本。
			  logseq.order-list-type:: number
			- `const`修饰版本。
			  logseq.order-list-type:: number
			- `volatile`修饰版本。
			  logseq.order-list-type:: number
			- `const volatile`修饰版本。
			  logseq.order-list-type:: number
		- [[数组]]类型被认为具有与其元素类型相同的 cv 修饰。
		- ## const 和 volatile 对象
			- 当对象首次创建时，使用的 cv 修饰符确定了对象的 constness 或 volatility ，如下所示：
				- const 对象是：
				  logseq.order-list-type:: number
					- 其类型经过`const`修饰，
					  logseq.order-list-type:: number
					- const 对象的非可变子对象。
					  logseq.order-list-type:: number
					- 这种对象无法被修改：直接尝试修改它会导致编译时错误，间接尝试修改（例如，通过 *引用* 或指向非 const 类型的 *指针* 修改 const 对象）会导致未定义行为。
				- volatile 对象是：
				  logseq.order-list-type:: number
					- 其类型经过volatile修饰，
					  logseq.order-list-type:: number
					- volatile 对象的子对象，
					  logseq.order-list-type:: number
					- const-volatile 对象的[[mutable]]子对象。
					  logseq.order-list-type:: number
					- 用 volatile 声明的类型变量表示可以被某些编译器未知的因素更改。比如：操作系统、硬件或者其它[[线程]]等。遇到这个关键字声明的变量，系统总是重新从它所在的内存读取数据，即使它前面的指令刚刚从该处读取过数据。即编译器对访问该变量的代码就不再进行优化，从而可以提供对特殊地址的稳定访问。
					- 通过非 volatile 类型的[[glvalue]]访问 volatile 对象的任何尝试（例如，通过非 volatile 类型的引用或指针）会导致[[未定义行为]]。
				- const-volatile 对象是：
				  logseq.order-list-type:: number
					- 其类型经过 const-volatile 修饰，
					  logseq.order-list-type:: number
					- const-volatile 对象的 non-[[mutable]]子对象
					  logseq.order-list-type:: number
					- volatile 对象的 const 子对象，
					  logseq.order-list-type:: number
					- const 对象的 non-[[mutable]] volatile 子对象。
					  logseq.order-list-type:: number
					- 它既表现为 const 对象又表现为 volatile 对象。
			- 每个 cv 修饰符（const 和 volatile）在任何 cv 修饰符序列中最多出现一次。
		- ## 具有 cv-修饰符的成员函数
			- 一个隐式对象的成员函数可以用[[cv-修饰符]]序列进行声明，这个序列出现在函数声明中的参数列表之后。
			  具有不同[[cv-修饰符]]序列的函数具有不同的类型，因此可以相互[[重载]]。
			- 在具有 cv-修饰符序列的成员函数体内，`*this`是带有 cv-修饰符的，例如，在具有 const 修饰符的成员函数中，**只有**具有 const 修饰符的其他成员函数可以被正常调用。如果应用了[[const_cast]]或者通过不涉及 this 的访问路径，没有 const 修饰符的成员函数仍然可以被调用。
			  id:: 652d4472-fec7-428e-9f19-aa0603194441
- ## [[mutable]]说明符
- ## 类型之间的转换
	- 对于引用和指针，可以隐式转换为更多 cv-修饰符的引用和指针，参阅 [qualification conversions](https://en.cppreference.com/w/cpp/language/implicit_cast#Qualification_conversions)
	- 要将对 cv 修饰的引用或指针转换为对更少 cv-修饰符的引用或指针，必须使用[[const_cast]]。
-