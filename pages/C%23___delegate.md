alias:: C# 委托

- C# 中的委托（Delegate）是一种数据结构，用于存储对方法的引用。它类似于 C 和 C++ 中的函数指针，但更安全和灵活。委托允许你将方法作为参数传递给其他方法，还可以用于定义回调方法和事件处理程序。
- ### 定义和使用委托
- #### 1. 定义委托
- 首先，你需要定义一个委托类型。委托类型声明指定了方法的签名，包括返回类型和参数类型。例如：
  ```csharp
  public delegate void MyDelegate(string message);
  ```
- 这个声明定义了一个名为 `MyDelegate` 的委托，它指向的任何方法都必须接受一个 `string` 参数并返回 `void`。
- #### 2. 实例化和调用委托
- 定义委托类型后，可以创建该类型的实例，并将其与符合签名的方法关联。然后，可以调用该委托，实际上是调用与其关联的方法。例如：
  ```csharp
  using System;
  
  public class Program
  {
    // 定义一个方法，与委托签名相匹配
    public static void PrintMessage(string message)
    {
        Console.WriteLine(message);
    }
  
    public static void Main()
    {
        // 实例化委托，并将其与方法关联
        MyDelegate del = new MyDelegate(PrintMessage);
        
        // 调用委托，实际上是调用关联的方法
        del("Hello, Delegate!");
    }
  }
  ```
- ### 多播委托
- 委托还可以多播，即一个委托实例可以包含多个方法的引用。当调用这个多播委托时，它将依次调用所有的方法。
  ```csharp
  using System;
  
  public class Program
  {
    public delegate void MyDelegate(string message);
  
    public static void PrintMessage(string message)
    {
        Console.WriteLine("Message: " + message);
    }
  
    public static void PrintUpperMessage(string message)
    {
        Console.WriteLine("Upper Message: " + message.ToUpper());
    }
  
    public static void Main()
    {
        MyDelegate del = PrintMessage;
        del += PrintUpperMessage;  // 添加另一个方法
  
        del("Hello, Delegate!");  // 调用委托，依次调用所有方法
    }
  }
  ```
- ### 使用委托进行回调
- 委托可以用于回调函数，在一个方法执行完成后调用另一个方法。
  ```csharp
  using System;
  
  public class Program
  {
    public delegate void MyDelegate(string message);
  
    public static void Process(string message, MyDelegate callback)
    {
        Console.WriteLine("Processing message: " + message);
        callback(message);  // 执行回调
    }
  
    public static void PrintMessage(string message)
    {
        Console.WriteLine("Callback message: " + message);
    }
  
    public static void Main()
    {
        MyDelegate del = new MyDelegate(PrintMessage);
        Process("Hello, Callback!", del);
    }
  }
  ```
- ### 使用内置委托类型
- C# 提供了两种常用的内置委托类型：`Action` 和 `Func`。
	- `Action`：用于没有返回值的方法。
	- `Func`：用于有返回值的方法。
- #### 示例：使用 `Action`
  ```csharp
  using System;
  
  public class Program
  {
    public static void PrintMessage(string message)
    {
        Console.WriteLine(message);
    }
  
    public static void Main()
    {
        Action<string> action = PrintMessage;
        action("Hello, Action!");
    }
  }
  ```
- #### 示例：使用 `Func`
  ```csharp
  using System;
  
  public class Program
  {
    public static int Add(int a, int b)
    {
        return a + b;
    }
  
    public static void Main()
    {
        Func<int, int, int> func = Add;
        int result = func(5, 3);
        Console.WriteLine("Result: " + result);
    }
  }
  ```
- ### 总结
	- 委托是 C# 中强大的特性，用于方法引用、回调和事件处理。通过使用委托，可以创建更灵活和可重用的代码。C# 还提供了内置的 `Action` 和 `Func` 委托类型，使得委托的使用更加简洁。