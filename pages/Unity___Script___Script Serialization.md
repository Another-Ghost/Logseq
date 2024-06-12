alias:: 脚本序列化

- 序列化是将数据结构或游戏对象状态自动转换为 Unity 可以存储和重建的格式的过程。
  在 Unity 项目中组织数据的方式会影响 Unity 如何序列化这些数据，从而对项目性能产生重大影响。此页面概述了 Unity 中的序列化及其优化方法。
- #### 序列化规则
  Unity 中的序列化器专门设计用于在运行时高效操作。因此，Unity 中的序列化行为与其他编程环境中的序列化不同。Unity 的序列化器直接作用于 C# 类的字段（fields）而不是属性，因此字段必须符合一些规则才能被序列化。以下部分概述了如何在 Unity 中使用字段序列化。
  要使用字段序列化，你必须确保字段：
	- 是 public 的，或者有 SerializeField 属性
	- 不是 static 的
	- 不是 const 的
	- 不是 readonly 的
- 字段类型可以序列化：
	- 原始数据类型（int、float、double、bool、string 等）
	- 枚举类型（32 位或更小）
	- 固定大小的缓冲区
	- Unity 内置类型，例如 Vector2、Vector3、Rect、Matrix4x4、Color、AnimationCurve
	- 带有 Serializable 属性的自定义结构体
	- 派生自 UnityEngine.Object 的对象引用
	- 带有 Serializable 属性的自定义类（见自定义类的序列化）
	- 上述字段类型的数组
	- 上述字段类型的 `List<T>`
	- **注意**：Unity 不支持多层类型的序列化（多维数组、锯齿数组、字典和嵌套容器类型）。如果需要序列化这些类型，有两种选择：
		- 将嵌套类型包装在类或结构体中
		- 通过实现 ISerializationCallbackReceiver 来使用序列化回调，进行自定义序列化。
- #### 自定义类的序列化
  要让 Unity 序列化自定义类，必须确保类：
	- 具有 Serializable 属性
	- 不是 static 的
- 当你将派生自 UnityEngine.Object 类的实例分配给一个字段并保存该字段时，Unity 将该字段序列化为对该实例的引用。Unity 会独立序列化该实例，因此当多个字段分配给该实例时不会重复。但对于不派生自 UnityEngine.Object 的自定义类，Unity 会将实例的状态直接包含在引用它们的 MonoBehaviour 或 ScriptableObject 的序列化数据中。 这可以通过两种方式发生：内联和 [SerializeReference]。
  **内联序列化**：默认情况下，如果你没有在引用类的字段上指定 [SerializeReference]，Unity 会按值内联序列化自定义类。这意味着如果你在多个字段中存储对自定义类实例的引用，它们在序列化时会变成独立的对象。然后，当 Unity 反序列化字段时，它们包含不同的独立对象但具有相同的数据。
  **[SerializeReference] 序列化**：如果指定了 [SerializeReference]，Unity 会将对象建立为托管引用。宿主对象仍然将对象直接存储在其序列化数据中，但在专用的注册表部分。
  [SerializeReference] 添加了一些开销，但支持以下情况：
	- 字段可以为空。内联序列化无法表示 null，而是用未分配字段的内联对象替代 null。
	- 多个引用同一个对象。如果在多个字段中存储对自定义类实例的引用而不使用 [SerializeReference]，它们在序列化时会变成独立的对象。
	- 图和循环数据（例如，一个对象引用回自己）。内联类序列化不支持 null 或共享引用，因此数据中的任何循环可能会导致意外结果，例如检查器行为异常、控制台错误或无限循环。
	- 多态性。如果创建一个派生自父类的类并将其分配给使用父类作为类型的字段，若不使用 [SerializeReference]，Unity 仅序列化属于父类的字段。当 Unity 反序列化类实例时，它会实例化父类而不是派生类。
	  当数据结构需要一个稳定的标识符来指向特定对象而不对对象的数组位置进行硬编码或搜索整个数组时，请参见 Serialization.ManagedReferenceUtility.SetManagedReferenceIdForObject。
	  **注意**：内联序列化更高效，除非明确需要 [SerializeReference] 支持的功能，否则应使用内联序列化。有关如何使用 [SerializeReference] 的详细信息，请参见 [SerializeReference 文档](https://docs.unity3d.com/Manual/SerializeReference.html)。
- ### 属性的序列化
  Unity 通常不序列化属性，除非在以下情况下：
	- 如果属性有一个显式的备份字段，Unity 会根据常规序列化规则序列化它。例如：
	  ```csharp
	  public int MyInt
	  {
	  get => m_backing;
	  private set => m_backing = value;
	  }
	  
	  [SerializeField] private int m_backing;
	  ```
	- Unity 仅在[[热重载]]期间序列化具有自动生成字段的属性。
	  ```csharp
	  public int MyInt { get; set; }
	  ```
	  如果不希望 Unity 序列化具有自动生成字段的属性，请使用 [field: NonSerialized] 属性。
	- ### 自定义序列化
	  有时你可能希望序列化 Unity 的序列化器不支持的内容（例如，C# 字典）。最好的方法是实现 ISerializationCallbackReceiver 接口。这允许你在序列化和反序列化过程中在关键点调用回调：
	- 当对象即将被序列化时，Unity 调用 OnBeforeSerialize() 回调。在此回调内部，可以将数据转换为 Unity 可以理解的格式。例如，要序列化 C# 字典，可以将数据从字典复制到键数组和值数组中。
	- 在 OnBeforeSerialize() 回调完成后，Unity 会序列化这些数组。
	- 之后，当对象被反序列化时，Unity 调用 OnAfterDeserialize() 回调。在此回调内部，可以将数据转换回适合内存中对象的形式。例如，使用键和值数组重新填充 C# 字典。
	- ## Unity 如何使用序列化
	- **保存和加载**：Unity 使用序列化来加载和保存场景、资源和 AssetBundles 到设备的内存中。这包括在你自己的脚本 API 对象（如 MonoBehaviour 组件和 ScriptableObject）中保存的数据。
	- **检查器（Inspector）窗口**：检查器窗口显示被检查对象的序列化字段的值。当你在检查器中更改一个值时，检查器会更新序列化数据并**触发反序列化**以更新被检查对象。
	- **[[热重载]]**：当你在编辑器中创建或编辑脚本并立即应用脚本行为时，称为热重载。无需重启编辑器即可使更改生效。当你更改并保存脚本时，Unity 会热重载所有当前加载的脚本数据。Unity 会存储所有可序列化变量，然后重新加载这些脚本并恢复序列化变量。热重载会丢弃所有不可序列化的数据，因此无法在此之后访问这些数据。
	- #### [[预制件]]
	  预制件是一个或多个游戏对象或组件的序列化数据。预制件实例包含对预制件源（source）和对其的修改列表的引用。修改是 Unity 需要对预制件源进行的操作，以创建特定的预制件实例。
	- #### 实例化
	  当你在场景中调用 Instantiate 来实例化预制件或游戏对象时：
		- Unity 会对其进行序列化。这发生在运行时和编辑器中。Unity 可以序列化所有派生自 UnityEngine.Object 的对象。
		- Unity 会创建一个新的游戏对象，并将数据反序列化到新游戏对象上。
		- Unity 会以不同的变体运行相同的序列化代码，以报告它引用的其他 UnityEngine.Object。它会检查所有引用的 UnityEngine.Object，查看它们是否是 Unity 实例化数据的一部分。如果引用指向外部内容（如纹理），Unity 会保留该引用。如果引用指向内部内容（如子游戏对象），Unity 会将引用修补到相应的副本。
	- #### 卸载未使用的资源
	  EditorUtility.UnloadUnusedAssetsImmediate 是 Unity 的本地垃圾回收器，目的与标准 C# 垃圾回收器不同。它在加载场景后运行，检查不再引用的对象（如纹理），并安全地卸载它们。本地 Unity 垃圾回收器会以一种变体运行序列化器，在这种变体中，对象报告所有对外部 UnityEngine.Object 的引用。这样可以卸载下一个场景中不再使用的纹理。
	- ### 编辑器和运行时序列化的区别
	  大多数序列化发生在编辑器中，而反序列化则在运行时进行。Unity 仅在编辑器中序列化某些功能，而在编辑器和运行时都可以序列化其他功能：
	  | 功能                                     | 编辑器         | 运行时         |
	  |----------------------------------------|--------------|--------------|
	  | 二进制格式的资源                         | 读/写支持     | 读支持        |
	  | YAML 格式的资源                         | 读/写支持     | 不支持        |
	  | 保存场景、预制件和其他资源               | 支持（除非在播放模式）| 不支持        |
	  | 使用 JsonUtility 序列化单个对象          | 使用 JsonUtility 读/写支持 | 使用 JsonUtility 读/写支持 |
	  | SerializeReference                    | 支持         | 支持         |
	  | ISerializationCallbackReceiver        | 支持         | 支持         |
	  | FormerlySerializedAs                  | 支持         | 不支持        |
	  对象可以有一些仅在编辑器中序列化的额外字段，例如在 UNITY_EDITOR 脚本符号中声明字段时：
	  ```csharp
	  public class SerializeRules : MonoBehaviour
	  {
	  #if UNITY_EDITOR
	  public int m_intEditorOnly;
	  #endif
	  }
	  ```
	  在上述示例中，m_intEditorOnly 字段仅在编辑器中序列化，不包含在构建中。这可以通过省略仅在编辑器中需要的数据来节省内存。使用该字段的任何代码也需要条件编译，例如在 \#if UNITY_EDITOR 块中，以便在构建时类可以编译。
	  编辑器不支持仅在运行时序列化字段的对象（例如，在 UNITY_STANDALONE 指令中声明字段时）。
	- #### 脚本序列化错误
	  脚本序列化可能导致错误。以下列出了一些修复方法。
	  “Find isn’t allowed to be called from a MonoBehaviour constructor (or instance field initializer), call in Awake or Start instead.”  
	  在 MonoBehaviour 构造函数或字段初始化器中调用 Scripting API（如 GameObject.Find）会触发此错误。
	  要修复此问题，请在 MonoBehaviour.Start 中调用 Scripting API，而不是在构造函数中。
	  “Find isn’t allowed to be called during serialization, call it from Awake or Start instead.”  
	  在标有 System.Serializable 的类的构造函数中调用 Scripting API（如 GameObject.Find）会触发此错误。
	  要修复此问题，请编辑代码，使其不在任何序列化对象的构造函数中调用 Scripting API。
	- #### 线程安全的 Unity 脚本 API
	  上述限制影响了大多数 Scripting API。只有一部分 Unity 脚本 API 是免除的，你可以在任何地方调用它们：
	- Debug.Log
	- Mathf 函数
	- 简单的自包含结构体；例如数学结构体，如 Vector3 和 Quaternion
	  为了减少序列化期间错误的风险，仅调用自包含的 API 方法，这些方法不需要获取或设置 Unity 本身的数据，除非没有其他选择。
	- #### 序列化最佳实践
	  你可以组织数据以确保最优地使用 Unity 的序列化。
	- 目标是让 Unity 序列化尽可能小的数据集。这样做的目的是确保你可以保持与项目早期版本的向后兼容性。处理大数据集的序列化在开发后期可能会变得更加困难。
	- 永远不要让 Unity 序列化重复数据或缓存数据。这会导致向后兼容性出现重大问题：因为数据可能不同步，所以错误风险很高。
	- 避免嵌套的递归结构，其中引用了其他类。序列化结构的布局始终需要相同；独立于数据，仅依赖于脚本中暴露的内容。引用其他类的唯一方法是通过派生自 UnityEngine.Object 的类。这些类是独立的；它们仅引用彼此，而不会嵌入内容。
	  <!--Converted by ToLogseq-->