alias:: value category

- 每个[[C++ 表达式]]具有两个独立的属性：[[type]]和[[value category]]。每个表达式都有某种[[非引用类型]]，并且每个表达式都属于三种主要值类别中的一种：[[prvalue]]、[[xvalue]]和[[lvalue]]。
	- 一个[[glvalue]]（“generalized” lvalue）是一个[[C++ 表达式]]，其[[求值]]确定了一个[[对象]]或[[函数]]的 [[identity]] 。
	- 一个[[prvalue]]（“pure” rvalue）是一个[[c++ 表达式]]，其求值：
		- 计算[[内置操作符]]的[[操作数]]的值（这种[[prvalue]]没有[[结果对象]]），或
		  logseq.order-list-type:: number
		  id:: 6532233a-ffe8-4b14-8abb-78bcb3f09751
		- [[初始化]]一个对象（这种[[prvalue]]被称为具有[[结果对象]]）。
		  logseq.order-list-type:: number
		- [[结果对象]]可以是一个[[变量]]，一个由[[new 表达式]]创建的对象，由[[temporary materialization]]创建的[[临时对象]]，或其成员。注意，非 void 类型的被弃值表达式也有一个结果对象（被材料化的临时对象）。此外，每个类和数组 prvalue 都有一个结果对象，除非它是 decltype 的操作数；
- 一个 xvalue（“即将过期”的值）是一个 glvalue，表示其资源可以被重用的对象；
- 一个 lvalue（因为在历史上，lvalues 可以出现在赋值表达式的左侧而得名）是一个不是 xvalue 的 glvalue；
- 一个 rvalue（因为在历史上，rvalues 可以出现在赋值表达式的右侧而得名）是一个 prvalue 或 xvalue。
  
  注意：这种分类法在过去的 C++ 标准修订中经历了重大变化，有关详细信息，请参阅下面的历史部分。