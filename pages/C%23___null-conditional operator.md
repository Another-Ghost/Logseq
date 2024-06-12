alias:: 空条件运算符

- C# 中的 `?.` 语法是空条件运算符（Null-conditional Operator），它用于简化对可能为 null 的对象的成员（属性、方法或索引器）的访问。使用 `?.` 可以避免显式的 null 检查，从而使代码更加简洁和易读。
- ### 用法
  当你使用 `?.` 访问对象的成员时，如果对象为 null，则整个表达式返回 null 而不会引发 `NullReferenceException`。如果对象不为 null，则正常访问该成员。
	- #### 示例
	  ```csharp
	  public class Person
	  {
	  public string Name { get; set; }
	  public Address HomeAddress { get; set; }
	  }
	  
	  public class Address
	  {
	  public string City { get; set; }
	  }
	  
	  public class Program
	  {
	  public static void Main()
	  {
	      Person person = null;
	  
	      // 使用 ?. 语法访问对象的成员
	      string cityName = person?.HomeAddress?.City;
	  
	      // 如果 person 为 null，cityName 将为 null，而不会引发 NullReferenceException
	      Console.WriteLine(cityName); // 输出：空 (null)
	  }
	  }
	  ```
	  在这个例子中，`person` 对象为 null，所以 `person?.HomeAddress` 结果为 null，进而 `person?.HomeAddress?.City` 也为 null。整个链式调用不会引发 `NullReferenceException`。
- ### 结合[[空合并运算符]] `??`
  通常，`?.` 会与空合并运算符 `??` 一起使用，以提供一个默认值。
  ```csharp
  public class Program
  {
    public static void Main()
    {
        Person person = null;
  
        // 使用 ?. 语法和 ?? 提供默认值
        string cityName = person?.HomeAddress?.City ?? "Unknown City";
  
        // 如果 person 为 null，cityName 将为 "Unknown City"
        Console.WriteLine(cityName); // 输出："Unknown City"
    }
  }
  ```
- ### 其他用法示例
	- **调用方法**：
	  logseq.order-list-type:: number```csharp
	  person?.DoSomething();
	  ```
	  如果 `person` 为 null，则 `DoSomething` 方法不会被调用。
	  - **访问数组或集合的元素**：
	  logseq.order-list-type:: number```csharp
	  int? length = array?.Length;
	  ```
	  如果 `array` 为 null，则 `length` 将为 null。
	- **处理事件**：
	  logseq.order-list-type:: number```csharp
	  myEvent?.Invoke(this, EventArgs.Empty);
	  ```
	  如果 `myEvent` 没有订阅者（即为 null），则不会触发事件。
- ### 总结
  `?.` 语法是 C# 中处理可能为 null 的对象的非常有用的工具。它可以避免繁琐的 null 检查，使代码更加简洁和易读。通过结合 `??` 运算符，可以提供默认值以确保代码的健壮性。
  <!--Converted by ToLogseq-->