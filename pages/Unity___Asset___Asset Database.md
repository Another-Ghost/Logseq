alias:: 资源数据库

- 对于大多数类型的资源，Unity 需要将资源的源文件中的数据转换为可用于游戏或实时应用程序的格式。这些转换后的文件及其关联的数据会存储在**资源数据库 (Asset Database)** 中。
- ### 源资源数据库
  源资源数据库包含有关源资源文件的元数据信息，Unity 将这些信息用来确定文件是否被修改，从而决定是否应该重新导入文件。这些信息中包括诸如上次修改日期、文件内容哈希、GUID 和其他元数据信息之类的信息。
- ### Artifact 数据库
  Artifact 是导入过程的结果。Artifact 数据库包含有关每个源资源的导入结果的信息。每个 Artifact 都包含导入依赖项信息、Artifact 元数据信息和 Artifact 文件列表。
- ## 导入资源
  Unity 通常会在资源被拖入项目时自动导入资源，但也可以在脚本控制下导入资源。为此，可以使用 [AssetDatabase.ImportAsset](https://docs.unity3d.com/cn/2021.1/ScriptReference/AssetDatabase.ImportAsset.html) 方法，如以下示例所示。
  ```
  using UnityEngine;
  using UnityEditor;
  
  public class ImportAsset {
    [MenuItem ("AssetDatabase/ImportExample")]
    static void ImportExample ()
    {
        AssetDatabase.ImportAsset("Assets/Textures/texture.jpg", ImportAssetOptions.Default);
    }
  }
  ```
  
  还可以将 [AssetDatabase.ImportAssetOptions](https://docs.unity3d.com/cn/2021.1/ScriptReference/ImportAssetOptions.html) 类型的额外参数传递给 AssetDatabase.ImportAsset 调用。
- ## 加载资源
  
  编辑器仅在需要时加载资源，例如，是否将资源添加到场景或从 Inspector 面板中进行编辑。但是，可以使用 [AssetDatabase.LoadAssetAtPath](https://docs.unity3d.com/cn/2021.1/ScriptReference/AssetDatabase.LoadAssetAtPath.html)、[AssetDatabase.LoadMainAssetAtPath](https://docs.unity3d.com/cn/2021.1/ScriptReference/AssetDatabase.LoadMainAssetAtPath.html)、[AssetDatabase.LoadAllAssetRepresentationsAtPath](https://docs.unity3d.com/cn/2021.1/ScriptReference/AssetDatabase.LoadAllAssetRepresentationsAtPath.html) 和 [AssetDatabase.LoadAllAssetsAtPath](https://docs.unity3d.com/cn/2021.1/ScriptReference/AssetDatabase.LoadAllAssetsAtPath.html) 从脚本加载和访问资源。有关更多详细信息，请参阅脚本文档。
  ```
  using UnityEngine;
  using UnityEditor;
  
  public class ImportAsset {
    [MenuItem ("AssetDatabase/LoadAssetExample")]
    static void ImportExample ()
    {
        Texture2D t = AssetDatabase.LoadAssetAtPath("Assets/Textures/texture.jpg", typeof(Texture2D)) as Texture2D;
    }
  }
  ```
- # 特殊文件夹名称
  通常可为创建的文件夹选择任何名称来组织 Unity 项目。但是，Unity 为特殊目的保留了一些文件夹名称。
- ## Assets
  **Assets** 文件夹是包含 Unity 项目使用的资源的主文件夹。Editor 中的 Project 窗口的内容直接对应于 Assets 文件夹的内容。大多数 API 函数都假定所有内容都位于 Assets 文件夹中，因此不要求显式提及该文件夹。但是，有些函数需要将 Assets 文件夹作为路径名的一部分添加（例如，[AssetDatabase](https://docs.unity3d.com/cn/2021.1/ScriptReference/AssetDatabase.html) 类中的一些函数）。
- ## Editor
  
  编辑器脚本在开发期间向 Unity 添加功能，但在运行时在构建中不可用。**Editor** 文件夹中的脚本以编辑器脚本的形式运行，而不是运行时脚本。
  
  可在 Assets 文件夹中的任何位置添加多个 Editor 文件夹。应将 Editor 脚本放在 Editor 文件夹内或其中的子文件夹内。
  
  Editor 文件夹的确切位置会影响其脚本相对于其他脚本的编译时间。参阅[特殊文件夹和脚本编译顺序](https://docs.unity3d.com/cn/2021.1/Manual/ScriptCompileOrderFolders.html)上的文档了解完整的描述。
  
  使用 Editor 脚本中的 [EditorGUIUtility.Load](https://docs.unity3d.com/cn/2021.1/ScriptReference/EditorGUIUtility.Load.html) 函数可从 Editor 文件夹中的 Resources 文件夹加载资源。这些资源只能通过 Editor 脚本加载，并会从构建中剥离。
  
  **注意：**如果脚本位于 Editor 文件夹中，Unity 不允许将派生自 MonoBehaviour 的组件分配给游戏对象。
- ## Editor Default Resources
  
  Editor 脚本可以使用通过 [EditorGUIUtility.Load](https://docs.unity3d.com/cn/2021.1/ScriptReference/EditorGUIUtility.Load.html) 函数按需加载的资源文件。此函数在名为 **Editor Default Resources** 的文件夹中查找资源文件。
  
  只能有一个 Editor Default Resources 文件夹，且必须将其放在项目的根目录中；直接位于 Assets 文件夹中。将所需的资源文件放在此 Editor Default Resources 文件夹内或其中的子文件夹内。如果资源文件位于子文件夹中，请始终在传递给 [EditorGUIUtility.Load](https://docs.unity3d.com/cn/2021.1/ScriptReference/EditorGUIUtility.Load.html) 函数的路径中包含子文件夹路径。
- ## Gizmos
  
  [Gizmos](https://docs.unity3d.com/cn/2021.1/ScriptReference/Gizmos.html) 允许将图形添加到 Scene 视图，以帮助可视化不可见的设计细节。[Gizmos.DrawIcon](https://docs.unity3d.com/cn/2021.1/ScriptReference/Gizmos.DrawIcon.html) 函数在场景中放置一个图标，作为特殊对象或位置的标记。必须将用于绘制此图标的图像文件放在名为 **Gizmos** 的文件夹中，这样才能被 DrawIcon 函数找到。
  
  只能有一个 Gizmos 文件夹，且必须将其放在项目的根目录，直接位于 Assets 文件夹中。将所需的资源文件放在此 Gizmos 文件夹内或其中的子文件夹内。如果资源文件位于子文件夹中，请始终在传递给 [Gizmos.DrawIcon](https://docs.unity3d.com/cn/2021.1/ScriptReference/Gizmos.DrawIcon.html) 函数的路径中包含子文件夹路径。
- ## Resources
  
  可从脚本中按需加载资源，而不必在场景中创建资源实例以用于游戏。为此，应将资源放在一个名为 **Resources** 的文件夹中。通过使用 [Resources.Load](https://docs.unity3d.com/cn/2021.1/ScriptReference/Resources.Load.html) 函数即可加载这些资源。
  
  可在 Assets 文件夹中的任何位置添加多个 Resources 文件夹。将所需的资源文件放在 Resources 文件夹内或其中的子文件夹内。如果资源文件位于子文件夹中，请始终在传递给 [Resources.Load](https://docs.unity3d.com/cn/2021.1/ScriptReference/Resources.Load.html) 函数的路径中包含子文件夹路径。
  
  **注意**：如果 Resources 文件夹是 Editor 的子文件夹，则其中的资源可通过 Editor 脚本加载，但会从构建中删除。
- ## StreamingAssets
	- 尽管将资源直接合并到构建中更为常见（但有时可能希望资源以其原始格式作为单独的文件提供）。例如，您需要使用 [Handheld.PlayFullScreenMovie](https://docs.unity3d.com/ScriptReference/Handheld.PlayFullScreenMovie.html) 从文件系统访问一个视频文件，以便在 IOS 上播放。
	  要包含流媒体资源，请执行以下操作：
		- 将文件放在 StreamingAssets 文件夹中。
		  logseq.order-list-type:: number
		- 该文件在复制到目标机器时保持不变，它可以从特定文件夹中获得。
		  logseq.order-list-type:: number
		  请参阅关于[流媒体资源](https://docs.unity3d.com/cn/2021.1/Manual/StreamingAssets.html)的页面以了解更多详细信息。
	- 只能有一个 StreamingAssets 文件夹，且必须将其放在项目的根目录，直接位于 Assets 文件夹中。将资源文件放在 StreamingAssets 文件夹或其子文件夹内。如果资源文件位于子文件夹中，请始终在用于引用流媒体资源的路径中包含子文件夹路径。
- ## 隐藏的资源
  
  在导入过程中，Unity 忽略 **Assets** 文件夹（或其子文件夹）中的以下文件和文件夹：
- 隐藏的文件夹。
- 以“**.**”开头的文件和文件夹。
- 以“**~**”结尾的文件和文件夹。
- 名为 **cvs** 的文件和文件夹。
- 扩展名为 **.tmp** 的文件。
  
  这可以防止导入由操作系统或其他应用程序创建的特殊文件和临时文件。