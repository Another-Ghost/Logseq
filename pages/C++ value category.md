alias:: value category

- 每个[[C++ 表达式]]具有两个独立的属性：[[type]]和[[value category]]。每个表达式都有某种[[非引用类型]]，并且每个表达式都属于三种主要值类别中的一种：[[prvalue]]、[[xvalue]]和[[lvalue]]。
	- 一个[[glvalue]]（“generalized” lvalue）是一个[[C++ 表达式]]，其[[求值]]确定了一个[[对象]]或[[函数]]的 [[identity]] 。
	- 一个[[prvalue]]（“pure” rvalue）是一个[[c++ 表达式]]，其求值：
		- 计算[[内置操作符]]的[[操作对象]]的值（这种[[prvalue]]没有[[结果对象]]），或
		  logseq.order-list-type:: number
		  id:: 6532233a-ffe8-4b14-8abb-78bcb3f09751
		- [[初始化]]一个对象（这种[[prvalue]]被称为具有[[结果对象]]）。
		  logseq.order-list-type:: number
		- [[结果对象]]可以是一个[[变量]]，一个由[[new 表达式]]创建的对象，由[[temporary materialization]]创建的[[临时对象]]，或其成员。注意，非`void`类型的[[discarded-value expression]]也有一个结果对象（[[materialized temporary]]）。此外，每个[[类]]和[[数组]][[prvalue]]都有一个[[结果对象]]，除非它是[[decltype]]的[[操作对象]]；
	- 一个[[xvalue]]（“eXpiring” value）是一个[[glvalue]]，表示其资源可以被重用的对象；
	- 一个[[lvalue]]（因为在历史上，[[lvalues]]可以出现在[[赋值表达式]]的左侧而得名）是一个不是[[xvalue]]的[[glvalue]]；
	- 一个[[rvalue]]（因为在历史上，[[rvalues]]可以出现在[[赋值表达式]]的右侧而得名）是一个[[prvalue]]或 [[xvalue]]。
-
- 在涉及到[[寻址]]、[[复制]]和[[移动]]对象时，有两个属性对于一个对象很重要：
	- 拥有[[identity]]：程序具有对象的[[名称]]、[[指针]]或[[引用]]，因此可以确定两个对象是否相同，对象的值是否发生了变化等。
	  logseq.order-list-type:: number
	  id:: 653231a7-9557-4ce6-9737-30376be2847f
	- [[movable]]：对象可以被[[移动]]（即，我们允许将其值移动到另一个位置，并将对象保留在一个有效但未指定状态，而不是[[复制]]对象）。
	  logseq.order-list-type:: number
- 事实证明，2 种属性的 4 种可能组合中的 3 种在精确描述 C++ 语言规则时是有用的（我们不需要既没有 identity 又不能移动的对象）。使用 "m" 表示可移动（movable），"i" 表示具有身份（has identity），我们可以以图形方式表示表达式的分类：
  id:: 65323569-8c52-4d88-83e0-13e440ef047f
  ![image.png](../assets/image_1697787998357_0.png)
- 因此，经典的[[lvalue]]是指具有[[身份]]但**不能**[[移动]]的东西（因为我们可以在移动之后检查它），而经典的[[rvalue]]则是可以[[移动]]的任何东西。其他替代方案包括 [[prvalue]]（"pure rvalue"，纯粹的 rvalue）、[[glvalue]]（"generalized lvalue"，广义的 lvalue）和[[xvalue]]（"x" 代表 "extraordinary" 或 "expert only"，有关这个 "x" 的含义的建议是非常有创意的）。例如：
  id:: 653249c9-0af4-4d47-a1a0-ac55cd81db31
- ```C++
  void f(vector<string>& vs)
  {
    vector<string>& v2 = std::move(vs); // 将 vs 移动到 v2
    // ...
  }
  ```
- 在这里，`std::move(vs)` 是一个[[xvalue]]：它明显具有身份（我们可以引用它作为 `vs`），但我们通过调用 `std::move()` 明确地允许它被[[移动]]。
- 对于实际编程来说，通常以[[rvalue]]和[[lvalue]]的术语思考已经足够。
  请注意，每个表达式要么是[[lvalue]]，要么是[[rvalue]]，而不会同时兼具两者。