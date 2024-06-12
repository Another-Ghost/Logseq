- `ScriptableObject` 是 Unity 中一种特殊的对象类型，用于存储独立于场景的^^可序列化数据^^。它们非常适合用来创建^^可重用的游戏数据^^，比如[[配置文件]]、共享资源、游戏参数等。与传统的 [[MonoBehaviour]] 不同，`ScriptableObject` 不需要附加到 GameObject 上。
- ### 使用 ScriptableObject 的步骤
- #### 1. 创建 ScriptableObject 类
	- 首先，你需要创建一个继承自 `ScriptableObject` 的类。以下是一个简单的示例：
	  ```csharp
	  using UnityEngine;
	  
	  [CreateAssetMenu(fileName = "NewCharacter", menuName = "Character")]
	  public class Character : ScriptableObject
	  {
	    public string characterName;
	    public int health;
	    public int damage;
	  }
	  ```
		- `CreateAssetMenu` 属性允许你在 Unity 编辑器的菜单中创建该 ScriptableObject 实例。
- #### 2. 创建 ScriptableObject 实例
	- **在 Unity 编辑器中**：
	  logseq.order-list-type:: number
		- 在项目窗口中右键点击，然后选择 `Create -> Character`（你自定义的菜单项）。
		- 这将创建一个新的 `Character` 实例，你可以在 Inspector 窗口中编辑其属性。
	- **通过代码创建**：
	  logseq.order-list-type:: number
	  如果你需要通过脚本创建一个 `ScriptableObject` 实例，可以使用以下代码：
	  ```csharp
	  using UnityEngine;
	  
	  public class CreateCharacter : MonoBehaviour
	  {
	  void Start()
	  {
	      Character newCharacter = ScriptableObject.CreateInstance<Character>();
	      newCharacter.characterName = "New Character";
	      newCharacter.health = 100;
	      newCharacter.damage = 25;
	  
	      // 可选：保存到资产文件中
	      #if UNITY_EDITOR
	      UnityEditor.AssetDatabase.CreateAsset(newCharacter, "Assets/NewCharacter.asset");
	      UnityEditor.AssetDatabase.SaveAssets();
	      #endif
	  }
	  }
	  ```
- #### 3. 使用 ScriptableObject
- 你可以在其他脚本中使用并访问 `ScriptableObject` 实例的数据。例如：
  ```csharp
  using UnityEngine;
  
  public class CharacterManager : MonoBehaviour
  {
    public Character character;
  
    void Start()
    {
        Debug.Log("Character Name: " + character.characterName);
        Debug.Log("Health: " + character.health);
        Debug.Log("Damage: " + character.damage);
    }
  }
  ```
	- 将 `Character` 实例拖动到 `CharacterManager` 组件的 `character` 属性上。
- ### ScriptableObject 的优点
	- **数据共享**：多个对象可以引用同一个 `ScriptableObject` 实例，实现数据共享。
	  logseq.order-list-type:: number
	- **项目管理**：将[[配置信息]]与[[脚本逻辑]]分离，便于管理和维护。
	  logseq.order-list-type:: number
	- **性能优化**：减少内存使用，因为 `ScriptableObject` 实例不会像 `MonoBehaviour` 那样附加到场景中的对象上。
	  logseq.order-list-type:: number
	- **序列化**：支持序列化和反序列化，方便在编辑器中进行保存和加载操作。
	  logseq.order-list-type:: number
- ### 示例应用
	- #### 配置文件
	- `ScriptableObject` 常用于存储配置文件，例如游戏设置、关卡数据、角色属性等。例如，创建一个用于存储游戏设置的 `ScriptableObject`：
	  ```csharp
	  using UnityEngine;
	  
	  [CreateAssetMenu(fileName = "GameSettings", menuName = "Settings/GameSettings")]
	  public class GameSettings : ScriptableObject
	  {
	    public float musicVolume;
	    public float sfxVolume;
	  }
	  ```
	- 然后在项目窗口中创建一个 `GameSettings` 实例，并在 Inspector 窗口中设置音量参数。接下来，可以在游戏代码中读取这些设置：
	  ```csharp
	  using UnityEngine;
	  
	  public class SettingsManager : MonoBehaviour
	  {
	    public GameSettings gameSettings;
	  
	    void Start()
	    {
	        AudioListener.volume = gameSettings.musicVolume;
	        // Apply other settings...
	    }
	  }
	  ```
	- #### 共享数据
	- 在多人游戏或复杂项目中，可以使用 `ScriptableObject` 来管理和共享数据，例如游戏物品、敌人属性等。例如，创建一个 `Item` ScriptableObject：
	  ```csharp
	  using UnityEngine;
	  
	  [CreateAssetMenu(fileName = "NewItem", menuName = "Inventory/Item")]
	  public class Item : ScriptableObject
	  {
	    public string itemName;
	    public Sprite icon;
	    public int maxStackSize;
	  }
	  ```
	- 然后，可以在多个脚本中引用并使用这些 `Item` 实例：
	  ```csharp
	  using UnityEngine;
	  using UnityEngine.UI;
	  
	  public class InventorySlot : MonoBehaviour
	  {
	    public Item item;
	    public Image icon;
	  
	    void Start()
	    {
	        if (item != null)
	        {
	            icon.sprite = item.icon;
	        }
	    }
	  }
	  ```
- ### 总结
	- `ScriptableObject` 是 Unity 中非常强大的数据存储工具，通过它可以有效地管理和共享游戏数据。无论是配置文件、游戏物品、角色属性还是其他共享数据，都可以使用 `ScriptableObject` 进行处理和优化。掌握 `ScriptableObject` 的使用，可以显著提升项目的结构和性能。
-