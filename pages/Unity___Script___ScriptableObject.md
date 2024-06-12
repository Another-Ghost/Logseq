- 如果你想创建独立于 GameObjects 存在的对象，可以派生自这个类。
  使用 ScriptableObjects 可以集中管理数据，方便项目中的场景和资源访问。
  使用 CreateInstance 实例化 ScriptableObject 对象。
  可以通过编辑器 UI 保存 ScriptableObjects 到资源文件（参见 CreateAssetMenuAttribute），或者通过脚本调用 AssetDatabase.CreateAsset。你也可以通过 ScriptedImporter 生成 ScriptableObjects 作为输出。参见 AssetImportContext.AddObjectToAsset。
  如果一个 ScriptableObject 没有被保存到资源文件，并且它被场景中的某个对象引用，Unity 会将它直接序列化到场景文件中。对于项目中只有一个持久实例的 ScriptableObject，可以使用 ScriptableSingleton<T0> 基类。
  使用 AssetDatabase 访问之前保存的对象，例如 AssetDatabase.LoadAssetAtPath。当一个 ScriptableObject 被 MonoBehaviour 字段引用时，ScriptableObject 会自动加载，因此脚本可以简单地使用该字段的值来访问它。
  ScriptableObject 的 C# 字段序列化方式与 MonoBehaviour 的字段完全相同。详情参见 Script Serialization。
  包含大数组或其他潜在大数据的类应该使用 PreferBinarySerialization 属性声明，因为 YAML 不是这种数据的高效表示形式。
  在 ScriptableObject 被销毁后，C# 对象会保留在内存中，直到垃圾回收。处于这种状态的 ScriptableObject 表现得像是 null。例如，对于“obj == null”检查会返回 true。然而，这个类不支持 null 条件运算符（`?.`）和 null 合并运算符（`??`）。
- ## 例子
  下面的示例展示了 ScriptableObject 的典型用法：不同类型的车辆参数表示在从 ScriptableObject 派生的 VehicleTypeInfo 类的字段中。每种类型的车辆都会有自己的资源文件，其参数值适当地设置为该类型。游戏中的每个车辆实例都会引用其类型对应的资源，而不是保留每个参数的冗余副本。这种设计方便在中央位置调整车辆行为，同时在共享数据量较大时也有助于提升性能。