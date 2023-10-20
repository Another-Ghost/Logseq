alias:: 隐式转换

- 隐式转换是在将值复制到兼容类型时自动执行的。例如：
- ``` cpp
  short a = 2000;
  int b;
  b = a;
  ```
- 在这里，变量 `a` 的值从 `short` 类型提升为 `int` 类型，无需任何显式操作符。这被称为[[标准转换]]。
  标准转换影响基本数据类型，允许不同[[数值类型]]之间的转换（如 `short` 到 `int`、`int` 到 `float`、`double` 到 `int` 等），以及与 `bool` 以及某些指针类型之间的转换。
- 从较小的整数类型转换为 `int`，或从 `float` 转换为 `double` 称为[[升级]]，并保证在目标类型中产生**相同**的值。
  id:: 65326d6e-30db-4da8-9653-83eef9748caf
  其他[[数值类型]]之间的转换可能无法精确表示相同的值：
	- 如果负整数值被转换为无符号类型，结果值对应于其二进制[[补码]]表示（即，-1 变成了类型可表示的最大值，-2 变成了第二大的值，依此类推）。
	- 从 `/` 到 `bool` 的转换将`false`视为等同于 0（对于[[数值类型]]），对于[[指针类型]]视为等同于[[空指针]]；`true`视为等同于所有其他值，并转换为等同于 1 的值。
	- 如果转换是从浮点类型到整数类型，值将被[[截断]]（去掉小数部分）。如果结果超出了目标类型可表示值的范围，转换将导致未定义行为。
	- 除此之外，如果转换是在相同类型的数值类型之间（整数到整数或浮点到浮点），则转换是有效的，但值是特定于实现的（并且可能不具有[[可移植性]]）。#TODO
- 其中一些转换可能涉及[[精度丢失]]，编译器可以发出警告。可以使用[[显式转换]]来避免这种警告。
- 对于非基本类型、数组和函数，它们会隐式地转换为指针，而指针通常允许以下转换：
	- [[空指针]]可以转换为任何类型的指针。
	- 任何类型的指针可以转换为[[void 指针]]。
	- 指针[[upcast]]：指向[[派生类]]的指针可以转换为指向可访问和明确的[[基类]]的指针，而不会修改其[[const]]或[[volatile]]修饰。
- # 类的隐式转换
	- 在[[类]]中，可以通过三个[[成员函数]]来控制[[隐式转换]]：
		- 单参数构造函数（single-argument [[constructors]]）：允许从特定类型进行隐式转换来初始化对象。
		  logseq.order-list-type:: number
		- 赋值操作符（[[assignment operator]]）：允许在赋值操作中从特定类型进行隐式转换。
		  logseq.order-list-type:: number
		- 类型转换操作符（[[type-cast operator]]）：允许进行隐式转换以获得特定类型。
		  logseq.order-list-type:: number
	- 示例：
	  id:: 653280eb-8e9c-4d9e-a740-511017191a15
	  
	  ``` cpp
	  // implicit conversion of classes:
	  #include <iostream>
	  using namespace std;
	  
	  class A {};
	  
	  class B {
	  public:
	    B (const A& x) {} // conversion from A (constructor)
	    B& operator= (const A& x) {return *this;} // conversion from A (assignment)
	    operator A() {return A();} // conversion to A (type-cast operator)
	  };
	  
	  int main ()
	  {
	    A foo;
	    B bar = foo;    // calls constructor
	    bar = foo;      // calls assignment
	    foo = bar;      // calls type-cast operator
	    return 0;
	  }
	  
	  ```
	- [[type-cast operator]] 使用特定的语法：它使用`operator`关键字，后面跟着目标类型和一对空括号。请注意，返回类型是**目标类型**，因此不需要在`operator`关键字之前指定。
	  id:: 653282b3-35e1-4874-8be2-df057d4d46d8
-
-