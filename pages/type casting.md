alias:: 类型转换, explicit conversion, 显式转换, type-casting, type-cast, 显式类型转换, explicit type-casting, 强制类型转换, 强制转换

- C++ 是一种强类型语言。许多转换，特别是那些涉及到值不同解释的情况，需要[[显式转换]]，C++ 中称为[[type-casting]]。有两种主要语法用于通用类型转换：[[functional type-casting]]和[[C-like type casting]]：
- ``` cpp
  double x = 10.3;
  int y;
  y = int(x);    // 函数式表示法
  y = (int)x;    // C 风格类型转换表示法
  ```
- 这些通用类型转换的功能对于大多数[[基本数据类型]]的需求足够了。然而，这些运算符可以无差别地应用于类和指向类的指针，这可能会导致在语法上正确但在运行时可能导致错误的代码。例如，以下代码会在没有错误的情况下编译：
- ```cpp
  #include <iostream>
  using namespace std;
  
  class Dummy {
    double i, j;
  };
  
  class Addition {
    int x, y;
  public:
    Addition(int a, int b) { x = a; y = b; }
    int result() { return x + y; }
  };
  
  int main() {
    Dummy d;
    Addition* padd;
    padd = (Addition*) &d;
    cout << padd->result();
    return 0;
  }
  ```
- 该程序声明了一个指向 *Addition* 的指针，但然后使用显式类型转换将其分配给了一个不相关类型的对象的引用：
  ```cpp
  padd = (Addition*) &d;
  ```
  不受限制的[[显式类型转换]]允许将任何指针转换为任何其他指针类型，独立于它们指向的类型。随后对成员 *result* 的调用将产生运行时错误或其他意外的结果。
- 为了控制类之间的这些类型转换，我们有四种特定的[[casting operators]]：[[dynamic_cast]]、[[reinterpret_cast]]、[[static_cast]]和[[const_cast]]。它们的格式是在尖括号（<>）之间跟随新类型，然后在括号内紧跟要转换的[[表达式]]。
- ``` cpp
  dynamic_cast<new_type>(expression)
  reinterpret_cast<new_type>(expression)
  static_cast<new_type>(expression)
  const_cast<new_type>(expression)
  ```
- 传统的类型转换等效于这些表达式的形式为：
  ``` cpp
  (new_type) expression
  new_type (expression)
  ```
  但每种类型转换都有自己的特殊特性。