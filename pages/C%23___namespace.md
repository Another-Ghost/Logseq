- 在 C# 中，`namespace`（命名空间）用于组织代码，并防止类、接口、枚举和委托等的命名冲突。命名空间是一个逻辑上的分组方式，可以帮助开发者管理和维护代码结构。
- ### 使用 `namespace`
- #### 1. 定义命名空间
- 命名空间的定义使用 `namespace` 关键字，后跟命名空间的名称，然后是一个包含相关类和其他类型定义的大括号块。
  ```csharp
  namespace MyProject.Utilities
  {
    public class UtilityClass
    {
        public void UtilityMethod()
        {
            // 方法实现
        }
    }
  }
  ```
- 在上面的例子中，`MyProject.Utilities` 是命名空间，`UtilityClass` 是定义在该命名空间中的一个类。
- #### 2. 使用命名空间
- 要使用特定命名空间中的类或其他类型，可以使用 `using` 关键字导入该命名空间。
  ```csharp
  using MyProject.Utilities;
  
  public class MainClass
  {
    public static void Main(string[] args)
    {
        UtilityClass utility = new UtilityClass();
        utility.UtilityMethod();
    }
  }
  ```
- 通过 `using MyProject.Utilities;`，我们可以在 `MainClass` 中直接使用 `UtilityClass`，而不需要每次都写完整的命名空间路径。
- ### 命名空间的嵌套
- 命名空间可以嵌套定义，从而形成层级结构。这对于大型项目特别有用。
  ```csharp
  namespace MyProject
  {
    namespace Utilities
    {
        public class UtilityClass
        {
            public void UtilityMethod()
            {
                // 方法实现
            }
        }
    }
  }
  ```
- 在这种情况下，可以使用嵌套命名空间的全名来引用类型，例如 `MyProject.Utilities.UtilityClass`。
- ### 使用别名
- 可以为命名空间创建别名，以简化引用长命名空间名称。
  ```csharp
  using Util = MyProject.Utilities;
  
  public class MainClass
  {
    public static void Main(string[] args)
    {
        Util.UtilityClass utility = new Util.UtilityClass();
        utility.UtilityMethod();
    }
  }
  ```
- 在这个例子中，我们为 `MyProject.Utilities` 命名空间创建了一个别名 `Util`，使得引用更简洁。
- ### 命名空间的最佳实践
	- **命名规范**：使用大写字母开头，且与项目名称和功能模块相关。例如：`MyProject.Utilities`。
	  logseq.order-list-type:: number
	- **避免冲突**：通过使用公司名称、项目名称等前缀来避免与第三方库或其他项目的命名空间冲突。
	  logseq.order-list-type:: number
	- **层级结构**：根据项目结构和模块功能合理设计命名空间的层级结构，便于维护和管理。
	  logseq.order-list-type:: number
- ### 示例
- 以下是一个包含多个命名空间和类的完整示例：
  ```csharp
  // 定义在 MyProject.Utilities 命名空间中的类
  namespace MyProject.Utilities
  {
    public class UtilityClass
    {
        public void UtilityMethod()
        {
            // 方法实现
        }
    }
  }
  
  // 定义在 MyProject.Models 命名空间中的类
  namespace MyProject.Models
  {
    public class DataModel
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }
  }
  
  // 主程序类，使用了不同的命名空间
  using MyProject.Utilities;
  using MyProject.Models;
  
  public class MainClass
  {
    public static void Main(string[] args)
    {
        UtilityClass utility = new UtilityClass();
        utility.UtilityMethod();
  
        DataModel model = new DataModel
        {
            Id = 1,
            Name = "Example"
        };
    }
  }
  ```
- 在这个示例中，我们定义了两个命名空间 `MyProject.Utilities` 和 `MyProject.Models`，分别包含一个类 `UtilityClass` 和 `DataModel`。主程序类 `MainClass` 使用了 `using` 语句来导入这些命名空间，从而能够轻松地实例化和使用这些类。
- ### 总结
- 命名空间是 C# 中组织代码的基本工具，帮助开发者防止命名冲突，并提高代码的可维护性和可读性。通过合理地使用命名空间，开发者可以创建结构清晰、易于管理的大型应用程序。