alias:: 预制件

- 带有预设 [Component]([[Unity/Component]]) 的 [[GameObject]] 模板。
- 在 Unity 中，Prefab 是一种非常重要的概念，它允许你创建、配置和存储 GameObject 及其相关组件的预制副本，可以在场景中多次实例化。这种方式不仅提高了开发效率，还保证了项目的一致性和可维护性。
- ### 什么是 Prefab
	- Prefab 是一个预制对象，它包含了一个 GameObject 及其所有子对象、[[Component]]和属性。你可以将一个 Prefab 视为一个模板，用来在场景中创建多个相同的对象实例。
- ### 创建和使用 Prefab
- #### 1. 创建 Prefab
	- **创建 GameObject**：
	  logseq.order-list-type:: number
		- 在场景中创建一个 GameObject，并为其添加所需的组件和子对象。
		- 例如，一个简单的立方体对象：```bash
		  logseq.order-list-type:: number
		   GameObject -> 3D Object -> Cube
		   ```
		  - **保存为 Prefab**：
		  logseq.order-list-type:: number
		     - 在项目窗口中，选择一个文件夹（例如 `Assets/Prefabs`），然后将场景中的 GameObject 拖到项目窗口中。这样就会创建一个 Prefab 资产。
		  -    例如：```bash
		   Assets -> Prefabs -> New Prefab
		   ```
- #### 2. 实例化 Prefab
	- **拖放实例化**：
	  logseq.order-list-type:: number
		- 你可以直接将 Prefab 从项目窗口拖放到场景中，从而在场景中创建该 Prefab 的实例。
	- **通过脚本实例化**：
	  logseq.order-list-type:: number
		- 你也可以通过脚本动态实例化 Prefab。
		- 示例脚本：
		  logseq.order-list-type:: number
		  ```csharp
		   using UnityEngine;
		  
		   public class PrefabSpawner : MonoBehaviour
		   {
		       public GameObject prefab;  // 需要在编辑器中分配此 Prefab
		  
		       void Start()
		       {
		           // 在位置 (0, 0, 0) 处实例化 Prefab
		           Instantiate(prefab, new Vector3(0, 0, 0), Quaternion.identity);
		       }
		   }
		  ```
		  将这个脚本附加到一个空的 GameObject 上，并在 Inspector 中将 `prefab` 属性设置为你创建的 Prefab。
- ### 编辑 Prefab
	- **编辑 Prefab**：
	  logseq.order-list-type:: number
	  双击项目窗口中的 Prefab，Unity 会进入 Prefab 编辑模式。在这种模式下，你可以对 Prefab 进行修改，所有的实例都会自动更新。
	  例如：
	   双击 Prefab -> 进入 Prefab 编辑模式
	- **应用更改**：
	  logseq.order-list-type:: number
		- 如果你在场景中的某个实例上做了修改，并希望将这些更改应用到 Prefab 上，可以在 Inspector 中点击 `Apply` 按钮。
- ### Prefab 的优点
	- **一致性**：Prefab 确保相同类型的对象具有一致的配置和外观。
	  logseq.order-list-type:: number
	- **复用性**：可以在多个场景中复用 Prefab，减少重复劳动。
	  logseq.order-list-type:: number
	- **维护性**：修改 Prefab 会自动更新所有实例，提高了维护效率。
	  logseq.order-list-type:: number
	- **性能优化**：通过批量实例化 Prefab，可以提高性能，特别是在需要创建大量相同对象的场景中。
	  logseq.order-list-type:: number
- ### Prefab Variants
	- Prefab Variants 是 Prefab 的扩展版本，允许你创建一个基于现有 Prefab 的变体。这样可以在保留原始 Prefab 基础设置的同时，添加或修改部分属性。
	- #### 创建 Prefab Variants
		- **选择原始 Prefab**：
		  logseq.order-list-type:: number
			- 在项目窗口中选择你想要创建变体的 Prefab。
		- **创建变体**：
		  logseq.order-list-type:: number
			- 右键点击选中的 Prefab，选择 `Create -> Prefab Variant`，这会创建一个基于原始 Prefab 的新变体。
		- **编辑变体**：
		  logseq.order-list-type:: number
			- 双击变体进入编辑模式，可以对变体进行修改，这些修改不会影响原始 Prefab。
- ## InstantiatingPrefabsExample
	- 以下脚本显示了如何使用 **Instantiate()** 函数来发射飞弹。
	  
	  ```
	  using UnityEngine;
	  public class FireProjectile : MonoBehaviour
	  {
	      public Rigidbody projectile;
	      public float speed = 4;
	      void Update()
	      {
	          if (Input.GetButtonDown("Fire1"))
	          {
	              Rigidbody p = Instantiate(projectile, transform.position, transform.rotation);
	              p.velocity = transform.forward * speed;
	          }
	      }
	  }
	  ```
	  
	  在代码中，预制件变量类型是刚体，而不是游戏对象。这样有两个有用的效果：
	- 只能为此变量分配具有刚体组件的游戏对象。这很有用，因为它有助于确保您为变量分配了正确的游戏对象。
	- Instantiate 方法返回对新实例上的刚体组件的引用。这很有用，因为这样可以轻松地在实例化刚体之后立即设置刚体的速度。
	-
- ### 总结
	- Prefab 是 Unity 中强大的工具，允许你创建、配置和管理可复用的对象模板。在开发中，Prefab 提供了更高的效率、一致性和可维护性。通过正确使用 Prefab 和 Prefab Variants，可以大大简化复杂项目的开发和管理。
- ## Reference
	- https://docs.unity3d.com/cn/2022.3/Manual/Prefabs.html
	- https://docs.unity3d.com/cn/current/Manual/InstantiatingPrefabs.html
	-