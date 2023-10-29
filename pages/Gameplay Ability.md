alias:: 玩法技能, Ability, 技能

- [[Gameplay Ability]]源自`UGameplayAbility`类，定义了游戏中技能的效果、使用技能付出的代价（如有），以及何时或在何情况下可以使用等。
  id:: 653e0d96-8189-45ef-81df-756bd46f3fa9
  Gameplay Ability 可以作为[[异步]]运行的实例化对象存在，因此你可以运行专门的多阶段任务，包括角色 *动画* 、*粒子* 和 *声效* ，乃至根据执行时的 用户输入 或 角色交互 设计分支。
  玩法技能可以在整个网络中自我[[复制]]，运行在客户端或服务器计算机上（包括客户端预测支持），甚至还能[[同步变量]]和执行[[RPC]]。
  Gameplay Ability 还可在游戏期间灵活实现游戏技能，例如提供的扩展功能可用于实现 *冷却* 和 *使用消耗* 、*玩家输入* 、使用 *动画蒙太奇* 的动画，以及对给予 Actor 的 *技能* 本身做出反应。
- # 授予（grant）和撤销(revoke)技能
	- 在Actor可以使用某项技能之前，必须向其[[Ability System Component]][[授予]]该技能。
	  [[Ability System Component]]的以下函数可以授予某项技能：
		- `GiveAbility`：使用[[FGameplayAbilitySpec]]指定要添加的技能，并返回[[FGameplayAbilitySpecHandle]]。
		  logseq.order-list-type:: number
		- `GiveAbilityAndActivateOnce`：使用 `FGameplayAbilitySpec` 指定要添加的技能，并返回 `FGameplayAbilitySpecHandle`。
		  logseq.order-list-type:: number
		  技能必须**实例化**，并且必须**能够在服务器上运行**。尝试在服务器上运行技能后，将返回 `FGameplayAbilitySpecHandle`。如果技能没有满足所需条件，或者无法执行，返回值将**无效**，并且技能系统组件将**不会被授予该技能**。
	- 以下函数可以利用授予技能后返回的[[FGameplayAbilitySpecHandle]]，来撤销对[[Ability System Component]]中的该技能。
		- `ClearAbility`: 从技能系统组件中移除指定技能。
- -
- `SetRemoveAbilityOnEnd`：当该技能执行完毕时，将该技能从技能系统组件中移除。如果未执行该技能，将立即移除它。如果正在执行该技能，将立即清除其输入，这样玩家就无法重新激活它或与它互动。
- -
- `ClearAllAbilities`：从技能系统组件中移除所有技能。此函数是唯一不需要 `FGameplayAbilitySpecHandle` 的函数。