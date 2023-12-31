alias:: vtbl, 虚函数表, vtable, virtual table

- 在C++中，[[虚函数表]]是一种用于支持[[运行时多态]]的机制。当[[类]]使用[[虚函数]]时，[[编译器]]会为该类以及它的派生类创建一个虚函数表。这个表是一个[[编译时]]构建的，包含指向类的 *虚函数的指针的数组* 。
  **每个拥有虚函数的类都有自己的虚函数表**。
- ### 工作原理
	- 1. **虚函数表**：每个拥有虚函数的类都有一个虚函数表。这个表是一个指针数组，每个指针指向一个虚函数的实现。
	- 2. **[[虚指针]]**：每个对象的实例都包含一个指向其类的虚函数表的指针（称为 虚指针 ）。这个指针是在[[对象构造时]]由[[构造函数]]设置的。
	- 3. **[[动态绑定]]**：当调用一个虚函数时，程序会使用对象中的虚指针来查找正确的虚函数表，然后通过这个表找到对应的函数实现，从而实现动态绑定。
- ### 示例
	- 假设我们有以下类结构：
	  ```cpp
	  class Base {
	  public:
	    virtual void func() { /* ... */ }
	  };
	  
	  class Derived : public Base {
	  public:
	    void func() override { /* ... */ }
	  };
	  ```
	  对于这个例子：
	- 编译器将为`Base`类创建一个虚函数表，其中包含`Base::func`的地址。
	- 对于`Derived`类，编译器也会创建一个虚函数表，但这个表中将包含`Derived::func`的地址。
	  
	  当我们这样使用这些类：
	  ```cpp
	  Base* b = new Derived;
	  b->func();
	  ```
	  
	  程序运行到`b->func();`时，它会通过`b`的虚指针找到`Derived`的虚函数表，并调用`Derived`类中`func`的实现。
- ### 重要性
  虚函数表使得C++支持运行时多态，这是面向对象编程的一个关键特性。它允许我们通过基类指针或引用调用派生类的方法，从而使得代码更加通用和灵活。
- ### 注意事项
	- **性能考虑**：虚函数表带来了轻微的性能成本，因为每次虚函数调用都需要额外的[[间接跳转]]。不过，对于大多数应用来说，这个成本是可以接受的。
	- **内存使用**：每个对象会因为虚指针而稍微增加一些内存占用。
- 虽然虚函数表的具体实现是编译器依赖的（并非C++标准的一部分），了解其基本概念对于理解C++中的多态和动态绑定非常重要。