- `dynamic_cast` 只能用于**类的指针和引用**（或 `void*`）。它的目的是确保类型转换的结果指向目标指针类型的有效完整对象。
- 这自然包括[[pointer upcast]]（从指向派生类的指针转换到指向基类的指针），就像[[隐式转换]]一样允许的。
- 但是 `dynamic_cast` 也可以将[[多态类]]（具有[[virtual members]]的类）的指针从基类向派生类进行[[downcast]]，但**仅当**指向的对象是**目标类型的**有效完整对象时。例如：
- ``` cpp
  //dynamic_cast
  #include <iostream>
  #include <exception>
  using namespace std;
  
  class Base { virtual void dummy() {} };
  class Derived: public Base { int a; };
  
  int main () {
  try {
    Base * pba = new Derived;
    Base * pbb = new Base;
    Derived * pd;
    pd = dynamic_cast<Derived*>(pba);
    if (pd==0) cout << "Null pointer on first type-cast. \n";
    pd = dynamic_cast<Derived*>(pbb);
    if (pd==0) cout << "Null pointer on second type-cast. \n";
   } catch (exception& e) {cout << "Exception: " << e.what();}
   return 0;
  }
  ```
- 兼容性说明：这种类型的 `dynamic_cast` 需要[[RTTI]]来跟踪[[动态类型]]。
  >一些编译器将此功能作为默认禁用的选项支持。必须启用这个选项，才能使 `dynamic_cast` 在这些类型上的运行时类型检查正常工作。
- 当 `dynamic_cast` 无法进行指针转换，因为它不是所需类的完整对象时（就像前面示例中的第二次转换一样），它返回一个 *空指针* 以指示失败。如果 `dynamic_cast` 用于转换为引用类型，而转换不可能，它会抛出 `bad_cast` 类型的 *异常*。
- >`dynamic_cast` 还可以执行允许在指针上进行的其他隐式转换：在不同指针类型之间转换空指针（甚至在不相关的类之间），以及将任何类型的指针转换为 `void*` 指针。
-