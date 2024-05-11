alias:: 函数对象, functor, 函子, 仿函数

- [[模板]]的一个特殊用途是[[函数对象]]，用这种机制定义的对象可以像函数一样调用。例如：
- ``` cpp
  template<typename T> 
  class Less_than
  {
  	const T val;//待比较的值
  public: 
  	Less_than(const T&v):val{v}{}
    	bool operator()(const T &x) const {return x<val;} //调用运算符；
  };
  ```
- TODO 其中，名为 `operator()` 的函数实现了“函数调用”或者称为“调用”或“应用”运算符 `()` 。可以为某些参数类型定义 `Less_than` 类型的命名变量：Less_than Iti{42};I/1ti（i）将用<比较i和42（i<42）Less_than Its{"Backus"s);I/ 1ts（s）将用<比较s和“Backus"（s<"Backus")Less_than<string> Its2{"Naur");I"Naur"是一个c风格字符串，因此要使用<string>来使用正确的<接下来，就能像调用函数一样调用这种对象了：void fct(int n,const string &s)sbool b1=Iti(n);II如果n<42，则为真bool b2=Its(s);II如果s<"Backus"，则为真II...
- ## [[匿名函数对象]]