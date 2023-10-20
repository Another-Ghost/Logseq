alias:: typeid

- `typeid` 允许检查表达式的[[type]]：
- ``` cpp
  typeid (type)
  typeid (expression)
  ```
- 这个运算符返回一个[[type_info]]类型的常量对象的引用，`type_info` 类型在标准头文件 `<typeinfo>` 中定义。
  id:: 6532afa5-a305-4e6b-8804-0b0a2924b25c
  `typeid` 返回的值可以与另一个 `typeid` 返回的值使用 `==` 和 `!=` 操作符进行比较，也可以用它的 `name()` 成员来获取表示数据类型或类名的以空字符结尾的字符序列。
- ``` cpp
  // typeid
  #include <iostream>
  #include <typeinfo>
  using namespace std;
  
  int main () {
  int * a,b;
  a=0; b=0;
  if (typeid(a) != typeid(b))
  {
    cout << "a and b are of different types:\n";
    cout << "a is: " << typeid(a).name() << '\n';
    cout << "b is: " << typeid(b).name() << '\n';
  }
  return 0;
  }
  ```
- 输出：
  
  ```
  a and b are of different types:
  a is: int *
  b is: int  
  ```
- 当 `typeid` 应用于类时，`typeid` 使用[[RTTI]]来跟踪[[动态]]对象的类型。当 `typeid` 应用于其类型为 *多态类* 的表达式时，结果是 *派生完整对象* 的类型：
  id:: 6532afa5-1e7d-4331-9c01-ae9a745e6d51
- ``` cpp
  // typeid, polymorphic class
  #include <iostream>
  #include <typeinfo>
  #include <exception>
  using namespace std;
  class Base { virtual void f(){} };
  class Derived : public Base {};
  int main () {
    try {
      Base* a = new Base;
      Base* b = new Derived;
      cout << "a is: " << typeid(a).name() << '\n';
      cout << "b is: " << typeid(b).name() << '\n';
      cout << "*a is: " << typeid(*a).name() << '\n';
      cout << "*b is: " << typeid(*b).name() << '\n';
    } catch (exception& e) { cout << "异常: " << e.what() << '\n'; }
  return 0;
  }
  ```
- 输出：
  ``` 
  a is: class Base *
  b is: class Base *
  *a is: class Base
  *b is: class Derived
  ```
- id:: 6532afa5-b7a7-42d4-9514-e843c2c7dbc7
  >注意：`type_info` 的 `name()` 成员返回的 *字符串* 依赖于编译器和库的**具体实现**。它不一定是一个简单的字符串，像在生成此输出的编译器中所示那样，具有典型的类型名称。
- 请注意，`typeid` 对于指针考虑的是[[指针类型]]本身（`a` 和 `b` 都属于 `class Base *` 类型）。然而，当 `typeid` 应用于对象（例如 `*a` 和 `*b`）时，`typeid` 返回它们的[[动态类型]]。
- 如果 `typeid` 求值的类型是由解引用操作符（`*`）引导的指针，并且该指针具有空值，`typeid` 将引发 [[bad_typeid]]异常。
  id:: 6532afa5-91e8-4b03-8ee8-5e0f7b2e0b95