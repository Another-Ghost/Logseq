- 在 C# 中，`new` 关键字用于创建新的对象实例或者隐藏基类中的成员。
- ### 创建新的对象实例 
  logseq.order-list-type:: number
  `new` 关键字可以用来创建新的对象实例，它通常用于类的构造函数中。
  ```csharp
  public class MyClass
  {
    public int MyProperty { get; set; }
  
    // 构造函数
    public MyClass()
    {
        MyProperty = 10;
    }
  }
  
  // 创建 MyClass 类的新实例
  MyClass myObject = new MyClass();
  ```
- ### 隐藏基类中的成员 
  logseq.order-list-type:: number
  在派生类中，可以使用 `new` 关键字隐藏基类中的同名成员，这样在派生类中就可以重新定义这个成员，而不会产生编译警告。
  ```csharp
  public class MyBaseClass
  {
    public void MyMethod()
    {
        Console.WriteLine("Base method");
    }
  }
  
  public class MyDerivedClass : MyBaseClass
  {
    // 隐藏基类中的同名方法
    public new void MyMethod()
    {
        Console.WriteLine("Derived method");
    }
  }
  
  MyDerivedClass myObject = new MyDerivedClass();
  myObject.MyMethod(); // 输出 "Derived method"
  ```
	- 需要注意的是，使用 `new` 关键字隐藏基类中的成员时，并不是对成员的覆盖，而是在派生类中创建了一个新的成员，这样只有通过派生类的实例才能调用这个新的成员，而通过基类的实例调用时，将会调用基类中的成员。因此，在实际应用中要注意潜在的混淆和歧义。
- ### 泛型参数的 `new()` 约束 
  logseq.order-list-type:: number
  在泛型类或方法中，可以使用 `new()` 约束来要求类型参数具有无参数的公共构造函数。
  ```csharp
  public class MyClass<T> where T : new()
  {
    // 创建类型 T 的新实例
    public T CreateInstance()
    {
        return new T();
    }
  }
  
  MyClass<MyClass> myObject = new MyClass<MyClass>();
  MyClass instance = myObject.CreateInstance();
  ```
- ### 总结
  `new` 关键字在 C# 中有多种用法，主要用于创建新的对象实例或隐藏基类中的成员。要根据具体的需求和上下文正确地使用 `new` 关键字，以避免产生歧义和错误。