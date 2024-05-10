alias:: 虚拟调用

- 在面向对象编程中，^^虚拟调用^^（virtual call）是一种通过指针或引用调用函数的机制，其中函数的具体实现在运行时确定，而不是在编译时。这是多态的一种实现方式，允许通过基类的指针或引用来调用派生类的方法。
- ### C++ 中的虚拟调用
	- 在 C++ 中，虚拟函数是使用 `virtual` 关键字在基类中声明的函数，派生类可以覆盖这些函数。当通过基类的指针或引用调用虚拟函数时，C++ 运行时会检查对象的实际类型，并调用适当的派生类中的函数。这是通过虚函数表（vtable）实现的，每个类有自己的虚函数表，其中存储了指向该类虚函数的指针。
- ### 示例
	- 以下是一个简单的例子，演示了 C++ 中虚拟函数的使用：
	  ```cpp
	  #include <iostream>
	  
	  class Base {
	  public:
	    virtual void print() {  // 声明虚函数
	        std::cout << "Base class print function" << std::endl;
	    }
	    virtual ~Base() {}  // 虚析构函数以确保派生类析构函数被调用
	  };
	  
	  class Derived : public Base {
	  public:
	    void print() override {  // 重写虚函数
	        std::cout << "Derived class print function" << std::endl;
	    }
	  };
	  
	  void callPrint(Base& obj) {
	    obj.print();  // 虚拟调用
	  }
	  
	  int main() {
	    Base b;
	    Derived d;
	    callPrint(b);  // 输出 "Base class print function"
	    callPrint(d);  // 输出 "Derived class print function"
	    return 0;
	  }
	  ```
	- 在这个例子中，`callPrint` 函数接受一个 `Base` 类型的引用并调用 `print` 方法。由于 `print` 是虚拟函数，所以实际调用的函数取决于传递给 `callPrint` 的对象的类型。
- ### 优点和缺点
- **优点：**
	- **灵活性**：虚拟调用允许在运行时根据对象的实际类型决定调用哪个函数，从而实现多态。
	- **可扩展性**：可以在不修改现有代码的基础上，通过添加新的派生类来扩展应用程序的功能。
- **缺点：**
	- **性能开销**：虚拟调用需要额外的时间来处理虚函数表的查找，可能比非虚拟调用慢。
	- **内存使用**：每个对象需要额外的空间来存储指向虚函数表的指针。
- 虚拟调用是 C++ 中实现接口和抽象类行为的基础，是面向对象编程中多态性的关键部分。正确使用虚拟调用可以使代码更加模块化和可重用，但也应当注意其对性能的潜在影响。
  <!--Converted by ToLogseq-->