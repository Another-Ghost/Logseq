- 在[[类定义]]内部，关键字 static 声明的成员不绑定到 类实例 。
- ## 语法
	- 静态成员的声明是包含关键字 static 的成员声明。关键字 static 通常出现在其他说明符之前，但其实可以出现在说明符序列的任何位置。
	- 任何静态数据成员和静态成员函数的名称必须与包含类的名称不同。
- ## 解释
	- 类的静态成员不与该类的对象关联：它们是具有[[静态存储期]]或[[线程存储期]]的 独立变量 或 普通函数 。
	- 关键字 static 仅用于类定义内部静态成员的声明，但不用于该静态成员的定义：
	  ```cpp
	  class X { static int n; }; // 声明（使用 'static'）
	  int X::n = 1;              // 定义（不使用 'static'）
	  ```
	  类体内的声明不是定义，可以声明成员为[[不完整类型]]（除 void 外），包括成员所声明的类型：
	  ```cpp
	  struct Foo;
	  
	  struct S
	  {
	    static int a[]; // 声明，不完整类型
	    static Foo x;   // 声明，不完整类型
	    static S s;     // 声明，不完整类型（在其自身定义内）
	  };
	  
	  int S::a[10]; // 定义，完整类型
	  struct Foo {};
	  Foo S::x;     // 定义，完整类型
	  S S::s;       // 定义，完整类型
	  ```
	  然而，如果声明使用[[constexpr]]或[[inline]]（自[[C++17]]起）说明符，则成员必须声明为[[完整类型]]。
- ## 引用静态成员
	- 要引用类 T 的静态成员 m，可以使用两种形式：限定名称 T::m 或成员访问表达式 E.m 或 E->m，其中 E 是分别计算为 T 或 T* 的表达式。在同一类作用域中，不需要限定：
	  ```cpp
	  struct X
	  {
	    static void f(); // 声明
	    static int n;    // 声明
	  };
	  
	  X g() { return X(); } // 返回 X 的某个函数
	  
	  void f()
	  {
	    X::f();  // X::f 是静态成员函数的限定名称
	    g().f(); // g().f 是引用静态成员函数的成员访问表达式
	  }
	  
	  int X::n = 7; // 定义
	  
	  void X::f() // 定义 
	  { 
	    n = 1; // 在此作用域中，X::n 可以作为 n 访问
	  }
	  ```
	  
	  静态成员遵守类成员访问规则（private、protected、public）。
- ## [[静态成员函数]]
	- 静态成员函数不与任何对象关联。调用时，它们没有[[this]]指针。
	- 静态成员函数不能是[[virtual]]的、[[const]]的、[[volatile]]的或[[ref-qualified]]的。
	- 静态成员函数的地址可以存储在[[普通函数指针]]中，但不能存储在[[成员函数指针]]中。
- ## [[静态数据成员]]
	- 静态数据成员不与任何对象关联。即使没有定义该类的对象，它们也存在。整个程序中只有一个静态数据成员的实例，具有[[静态存储期]]，除非使用了关键字[[thread_local]]，这种情况下每个线程有一个此类对象，具有[[线程存储持续期]]。
	- 命名空间作用域中的类的静态数据成员如果 类本身具有[[外部链接]]（不是未命名命名空间的成员），则具有外部链接。[[local class]]（在函数内部定义的类）和未命名类，包括未命名类的成员类，不能有静态数据成员。
	- 静态数据成员可以声明为 inline。内联静态数据成员 可以在类定义中定义，并且可以指定初始化器。它不需要类外定义：
	  ```cpp
	  struct X
	  {
	    inline static int n = 1;
	  };
	  ```
	- ### 常量静态成员
		- 如果静态数据成员是 整数 或 枚举类型 的[[const]]（且不是[[volatile]]），则可以在类定义中用初始化器初始化，其中每个表达式都是常量表达式：
		  ```cpp
		  struct X
		  {
		  	const static int n = 1;
		  	const static int m{2}; // 自 C++11 起
		  	const static int k;
		  };
		  const int X::k = 3;
		  ```
		  如果静态数据成员是[[LiteralType]]并声明为[[constexpr]]，则必须在类定义中用初始化器初始化，其中每个表达式都是常量表达式：
		  ```cpp
		  struct X
		  {
		  	constexpr static int arr[] = { 1, 2, 3 };        // OK
		  	constexpr static std::complex<double> n = {1,2}; // OK
		  	constexpr static int k; // 错误：constexpr static 需要初始化器
		  };
		  ```
		  
		  如果 const 非内联（自 C++17 起）静态数据成员或 constexpr 静态数据成员（自 C++11 起）（直到 C++17）被 odr-use，则仍然需要在命名空间作用域进行定义，但不能有初始化器。
		  
		  constexpr 静态数据成员隐式地是内联的，不需要在命名空间作用域重新声明。这种不带初始化器的重新声明（以前是必需的）仍然被允许，但已被弃用。
		  
		  ```cpp
		  struct X
		  {
		    static const int n = 1;
		    static constexpr int m = 4;
		  };
		  
		  const int *p = &X::n, *q = &X::m; // X::n 和 X::m 被 odr-use
		  const int X::n;             // … 因此需要定义
		  constexpr int X::m;         // … （除了 C++17 中的 X::m）
		  ```