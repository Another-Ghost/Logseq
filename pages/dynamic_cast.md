- `dynamic_cast` 只能用于**类的指针和引用**（或 `void*`）。它的目的是确保类型转换的结果指向目标指针类型的有效完整对象。
- 这自然包括[[pointer upcast]]（从指向派生类的指针转换到指向基类的指针），就像[[隐式转换]]一样允许的。
- 但是 `dynamic_cast` 也可以将多态类（具有虚拟成员的类）的指针从基类向派生类进行向下转型，**但仅当**指向的对象是目标类型的有效完整对象时。例如：
- ```
  cppCopy code
  - #include <iostream>
  #include <exception>
  using namespace std;
  - class Base { virtual void dummy() {} };
  class Derived: public Base { int a; };
  - int main () {
  try {
    Base * pba = new Derived;
    Base * pbb = new Base;
    Derived * pd;
  - pd = dynamic_cast<Derived*>(pba);
    if (pd==0) cout << "第一次类型转换为null指针。\n";
  - pd = dynamic_cast<Derived*>(pbb);
    if (pd==0) cout << "第二次类型转换为null指针。\n";
  - } catch (exception& e) {cout << "异常: " << e.what();}
  return 0;
  }
  ```
- 兼容性说明：这种类型的 `dynamic_cast` 需要运行时类型信息（RTTI）来跟踪动态类型。一些编译器将此功能作为默认禁用的选项支持。必须启用这个选项，才能使 `dynamic_cast` 在这些类型上的运行时类型检查正常工作。
- 上面的代码尝试从类型为 `Base*` 的指针对象（`pba` 和 `pbb`）执行两次 `dynamic_cast`，将它们转换为类型为 `Derived*` 的指针对象，但只有第一个转换成功。请注意它们各自的初始化方式：
- ```
  cppCopy code
  - Base * pba = new Derived;
  Base * pbb = new Base;
  ```
- 尽管它们都是类型为 `Base*` 的指针，`pba` 实际上指向了一个 `Derived` 类型的对象，而 `pbb` 指向了一个 `Base` 类型的对象。因此，当使用 `dynamic_cast` 执行它们各自的类型转换时，`pba` 指向 `Derived` 类的一个完整对象，而 `pbb` 指向 `Base` 类的一个对象，这是 `Derived` 类的一个不完整对象。
- 当 `dynamic_cast` 无法进行指针转换，因为它不是所需类的完整对象时（就像前面示例中的第二次转换一样），它返回一个空指针以指示失败。如果 `dynamic_cast` 用于转换为引用类型，而转换不可能，它会抛出 `bad_cast` 类型的异常。
- `dynamic_cast` 还可以执行允许在指针上进行的其他隐式转换：在不同指针类型之间转换空指针（甚至在不相关的类之间），以及将任何类型的指针转换为 `void*` 指针。