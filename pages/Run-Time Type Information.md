alias:: RTTI, 运行时类型信息

- 在C++中，RTTI（Run-Time Type Information）是一种在程序[[运行时]]获取[[对象类型信息]]的机制。RTTI主要用于动态类型检查，它允许程序在运行时确定对象的实际数据类型。这对于使用了[[多态]]特性的编程语言来说尤为重要，因为在多态中，基类的指针或引用可能实际上指向派生类的对象。
- ### RTTI的关键特性
	- 1. **[[typeid]]运算符**：用于获取对象的类型信息。`typeid`与一个对象或类型一起使用时，会返回一个`std::type_info`对象，该对象提供了关于类型的信息，如类型的名称。
	- 2. **[[dynamic_cast]]运算符**：用于安全地将基类指针或引用转换为派生类指针或引用。`dynamic_cast`在转换不合法时会失败（返回空指针或抛出异常），从而提供了一种安全的向下转型方式。
- ### 示例
	- #### 使用`typeid`
	  
	  ```cpp
	  #include <iostream>
	  #include <typeinfo>
	  
	  class Base {
	  public:
	    virtual ~Base() {}
	  };
	  
	  class Derived : public Base {};
	  
	  int main() {
	    Base* base = new Derived;
	    
	    // 使用typeid获取对象的实际类型
	    std::cout << "The type of base is: " << typeid(*base).name() << std::endl;
	  
	    delete base;
	    return 0;
	  }
	  ```
	  
	  在这个示例中，即使`base`是一个`Base`类型的指针，但由于它实际上指向`Derived`对象，`typeid(*base)`将返回`Derived`的类型信息。
- #### 使用`dynamic_cast`
  
  ```cpp
  Base* base = new Derived;
  Derived* derived = dynamic_cast<Derived*>(base);
  
  if (derived) {
    // 成功转换
  } else {
    // 转换失败
  }
  ```
  
  在这个例子中，`dynamic_cast`尝试将`Base`类型的指针`base`转换为`Derived`类型的指针。如果`base`实际上指向一个`Derived`对象，转换成功，否则`derived`将为`nullptr`。
- ### 注意事项
  
  1. **性能影响**：RTTI的使用可能会带来性能上的开销，尤其是`dynamic_cast`运算符，因为它在运行时需要进行类型检查。
  
  2. **类型安全**：`dynamic_cast`比较安全，因为它在类型转换不正确时不会产生不确定的行为。
  
  3. **多态类**：`typeid`和`dynamic_cast`通常在涉及多态的类（即包含虚函数的类）中使用。
  
  总之，RTTI在C++中提供了一种机制，允许程序在运行时检查和确定对象的类型。虽然它非常有用，特别是在需要处理复杂的多态关系时，但它也可能带来一定的性能成本，因此应谨慎使用。