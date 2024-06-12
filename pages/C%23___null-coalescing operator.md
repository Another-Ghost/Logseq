alias:: 空合并运算符

- C# 中的 `??` 运算符称为**空合并运算符**（null-coalescing operator）。它用于在操作可能为 `null` 的值时提供一个默认值。如果左操作数为 `null`，则返回右操作数；否则，返回左操作数。
- ### 基本语法
  ```csharp
  var result = nullableValue ?? defaultValue;
  ```
	- `nullableValue`：可能为 `null` 的值。
	- `defaultValue`：当 `nullableValue` 为 `null` 时返回的值。
- ### 示例
  以下是一些使用 `??` 运算符的示例：
	- #### 示例 1：基本用法
	  ```csharp
	  string name = null;
	  string displayName = name ?? "Default Name";
	  Console.WriteLine(displayName); // 输出："Default Name"
	  ```
	  在这个例子中，因为 `name` 为 `null`，所以 `displayName` 被赋值为 `"Default Name"`。
	- #### 示例 2：非空值
	  ```csharp
	  string name = "Alice";
	  string displayName = name ?? "Default Name";
	  Console.WriteLine(displayName); // 输出："Alice"
	  ```
	  在这个例子中，因为 `name` 不为 `null`，所以 `displayName` 被赋值为 `"Alice"`。
	- #### 示例 3：结合 `?.` 运算符
	  ```csharp
	  public class Person
	  {
	  public string Name { get; set; }
	  }
	  
	  public class Program
	  {
	  public static void Main()
	  {
	      Person person = null;
	      string personName = person?.Name ?? "Unknown Person";
	      Console.WriteLine(personName); // 输出："Unknown Person"
	  }
	  }
	  ```
	  在这个例子中，`person` 为 `null`，所以 `person?.Name` 的结果为 `null`，然后 `??` 运算符将其替换为 `"Unknown Person"`。
- ### 嵌套使用 `??`
  你可以嵌套使用 `??` 运算符来处理多个可能为 `null` 的值：
  ```csharp
  string firstChoice = null;
  string secondChoice = null;
  string thirdChoice = "Third Choice";
  
  string result = firstChoice ?? secondChoice ?? thirdChoice ?? "Default Choice";
  Console.WriteLine(result); // 输出："Third Choice"
  ```
  在这个例子中，`firstChoice` 和 `secondChoice` 都为 `null`，所以返回 `thirdChoice` 的值 `"Third Choice"`。
- ### 常见用法
	- **默认参数**：在方法调用时提供默认参数值。
	  logseq.order-list-type:: number
	- **读取配置**：从配置中读取值，如果配置未设置则使用默认值。
	  logseq.order-list-type:: number
	- **处理可能为 `null` 的返回值**：例如数据库查询、API 调用等。
	  logseq.order-list-type:: number
- ### 总结
  `??` 运算符是 C# 中处理 `null` 值的一个便捷工具。它通过提供一个默认值来简化代码，并确保在遇到 `null` 值时不会导致程序崩溃。结合 `?.` 运算符，可以更高效地处理复杂的 `null` 值检查和赋值操作。