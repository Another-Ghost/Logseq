alias:: 特性

- **特性 (Attribute)** 是可以放在脚本中的类、属性或函数上方来指示特殊行为的标记。例如，可以将 `HideInInspector` 特性添加到属性声明上方，从而防止 Inspector 显示该属性（即使是公共属性）。C# 在方括号内包含特性名称，如下所示：
  
  ```
  [HideInInspector]
  public float strength;
  ```
  
  Unity 提供了在 API 参考文档中列出的大量特性：
- 对于 UnityEngine 特性，请参阅 [AddComponentMenu](https://docs.unity3d.com/cn/current/ScriptReference/AddComponentMenu.html) 和同级页面
- 对于 UnityEditor 特性，请参阅 [CallbackOrderAttribute](https://docs.unity3d.com/cn/current/ScriptReference/CallbackOrderAttribute.html) 和同级页面
  
  .NET 库中还定义了一些有时可能在 Unity 代码中很有用的特性。请参阅 [Microsoft 关于特性 (Attributes) 的文档](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/)以了解更多信息。
  
  **注意：**不要使用 .NET 库中定义的 [ThreadStatic](http://msdn.microsoft.com/en-us/library/system.threadstaticattribute.aspx) 特性；如果将其添加到 Unity 脚本，会导致崩溃。