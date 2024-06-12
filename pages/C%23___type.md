- 在 C# 中，类型（Type）是编程语言的核心概念之一。类型定义了变量可以存储的数据以及可以对这些数据执行的操作。C# 提供了多种类型，包括内置类型、用户定义类型和复杂类型。以下是对 C# 类型的详细介绍：
- ### 值类型（Value Types） 
  logseq.order-list-type:: number
	- 值类型直接包含其数据，分配在堆栈上。常见的值类型包括：
	- #### 内置值类型
		- **整数类型**：`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`
		- **浮点类型**：`float`, `double`
		- **十进制类型**：`decimal`
		- **字符类型**：`char`
		- **布尔类型**：`bool`
		  ```csharp
		  int integer = 42;
		  float floatingPoint = 3.14f;
		  bool boolean = true;
		  char character = 'A';
		  ```
	- #### 枚举（enum）
		- 枚举是一种特殊的值类型，用于定义一组命名常量。
		  ```csharp
		  public enum DaysOfWeek
		  {
		    Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday
		  }
		  
		  DaysOfWeek today = DaysOfWeek.Wednesday;
		  ```
	- #### 结构体（struct）
		- 结构体是值类型，用于封装相关的变量。
		  ```csharp
		  public struct Point
		  {
		    public int X;
		    public int Y;
		  
		    public Point(int x, int y)
		    {
		        X = x;
		        Y = y;
		    }
		  }
		  
		  Point p = new Point(10, 20);
		  ```
- ### 引用类型（Reference Types） 
  logseq.order-list-type:: number
	- 引用类型存储对象的引用，分配在堆上。常见的引用类型包括：
	- #### 类（class）
	- 类是引用类型，用于封装数据和方法。
	  ```csharp
	  public class Person
	  {
	    public string Name { get; set; }
	    public int Age { get; set; }
	  
	    public Person(string name, int age)
	    {
	        Name = name;
	        Age = age;
	    }
	  }
	  
	  Person person = new Person("Alice", 30);
	  ```
	- #### 接口（interface）
	- 接口定义一组方法和属性，供类实现。
	  ```csharp
	  public interface IMovable
	  {
	    void Move();
	  }
	  
	  public class Car : IMovable
	  {
	    public void Move()
	    {
	        Console.WriteLine("The car is moving");
	    }
	  }
	  
	  IMovable movable = new Car();
	  movable.Move();
	  ```
	- #### 数组（Array）
	- 数组是引用类型，可以存储相同类型的多个元素。
	  ```csharp
	  int[] numbers = new int[] { 1, 2, 3, 4, 5 };
	  string[] names = { "Alice", "Bob", "Charlie" };
	  ```
	- #### 字符串（String）
	- 字符串是不可变的引用类型，用于表示文本。
	  ```csharp
	  string greeting = "Hello, World!";
	  ```
	- #### 委托（Delegate）
	- 委托是引用类型，表示对方法的引用。
	  ```csharp
	  public delegate void MyDelegate(string message);
	  
	  public class MyClass
	  {
	    public void PrintMessage(string message)
	    {
	        Console.WriteLine(message);
	    }
	  }
	  
	  MyClass obj = new MyClass();
	  MyDelegate del = new MyDelegate(obj.PrintMessage);
	  del("Hello, Delegate!");
	  ```
	- #### 动态类型（dynamic）
	- 动态类型在运行时进行类型检查，允许更灵活的编程。
	  ```csharp
	  dynamic dyn = "Hello, Dynamic";
	  Console.WriteLine(dyn);
	  dyn = 12345;
	  Console.WriteLine(dyn);
	  ```
- ### 空类型（Nullable Types） 
  logseq.order-list-type:: number
	- 空类型用于表示可为空的值类型。使用 `?` 符号定义空类型。
	  ```csharp
	  int? nullableInt = null;
	  nullableInt = 42;
	  if (nullableInt.HasValue)
	  {
	    Console.WriteLine(nullableInt.Value);
	  }
	  ```
- ### 类型转换（Type Conversion） 
  logseq.order-list-type:: number
	- C# 提供了多种类型转换的方法，包括隐式转换、显式转换和类型转换方法。
	- #### 隐式转换
	- 编译器自动执行的安全转换。
	  ```csharp
	  int i = 123;
	  double d = i;  // 隐式转换
	  ```
	- #### 显式转换
	- 使用强制转换操作符执行的需要显式指定的转换。
	  ```csharp
	  double d = 123.45;
	  int i = (int)d;  // 显式转换
	  ```
	- #### 类型转换方法
	- 使用 `Convert` 类进行的类型转换。
	  ```csharp
	  string str = "123";
	  int i = Convert.ToInt32(str);
	  ```
- ### 类型检查和类型转换 
  logseq.order-list-type:: number
	- 使用 `is` 关键字检查对象的类型，使用 `as` 关键字进行安全的类型转换。
	  ```csharp
	  object obj = "Hello, World!";
	  if (obj is string)
	  {
	    string str = obj as string;
	    Console.WriteLine(str);
	  }
	  ```
- ### 总结
	- C# 提供了丰富的类型系统，涵盖了值类型、引用类型、空类型和复杂类型。理解和正确使用这些类型对于编写高效、可靠和可维护的 C# 程序至关重要。
	  <!--Converted by ToLogseq-->