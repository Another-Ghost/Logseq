alias:: 玩法技能, Ability, 技能

- [[Gameplay Ability]]源自`UGameplayAbility`类，定义了游戏中技能的效果、使用技能付出的代价（如有），以及何时或在何情况下可以使用等。
  id:: 653e0d96-8189-45ef-81df-756bd46f3fa9
  Gameplay Ability 可以作为[[异步]]运行的实例化对象存在，因此你可以运行专门的多阶段任务，包括角色 *动画* 、*粒子* 和 *声效* ，乃至根据执行时的 用户输入 或 角色交互 设计分支。
  玩法技能可以在整个网络中自我[[复制]]，运行在客户端或服务器计算机上（包括客户端预测支持），甚至还能[[同步变量]]和执行[[RPC]]。
  Gameplay Ability 还可在游戏期间灵活实现游戏技能，例如提供的扩展功能可用于实现 *冷却* 和 *使用消耗* 、*玩家输入* 、使用 *动画蒙太奇* 的动画，以及对给予 Actor 的 *技能* 本身做出反应。
- # 授予（grant）和撤销(revoke)技能
	- 在Actor可以使用某项技能之前，必须向其[[Ability System Component]] [[授予]]该技能。
	  [[Ability System Component]]的以下函数可以授予某项技能：
		- `GiveAbility`：使用[[FGameplayAbilitySpec]]指定要添加的技能，并返回[[FGameplayAbilitySpecHandle]]。
		  logseq.order-list-type:: number
		- `GiveAbilityAndActivateOnce`：使用 `FGameplayAbilitySpec` 指定要添加的技能，并返回 `FGameplayAbilitySpecHandle`。
		  logseq.order-list-type:: number
		  技能必须**实例化**，并且必须**能够在服务器上运行**。尝试在服务器上运行技能后，将返回 `FGameplayAbilitySpecHandle`。如果技能没有满足所需条件，或者无法执行，返回值将**无效**，并且技能系统组件将**不会被授予该技能**。
	- 以下函数可以利用授予技能后返回的[[FGameplayAbilitySpecHandle]]，来[[撤销]]对[[Ability System Component]]中的该技能。
		- `ClearAbility`: 从`Ability System Component`中移除指定技能。
		  logseq.order-list-type:: number
		- `SetRemoveAbilityOnEnd`：当该技能执行完毕时，将该技能从`Ability System Component`中移除。
		  logseq.order-list-type:: number
		  如果**未执行**该技能，将**立即移除它**。如果**正在执行**该技能，将**立即清除其输入**，这样玩家就无法重新激活它或与它互动。
		- `ClearAllAbilities`：从`Ability System Component`中移除所有技能。
		  logseq.order-list-type:: number
		  >此函数是**唯一**不需要[[FGameplayAbilitySpecHandle]]的函数。
- # 基本用法
	- 将Gameplay Ability 授予Actor的`Ability System Component`后，[[Ability]]的基本执行生命周期如下：
		- 即使调用者没有尝试执行某项技能，[[CanActivateAbility]]也可以让调用者知道是否可执行该技能。
		  logseq.order-list-type:: number
		- [[CallActivateAbility]]执行技能相关的游戏代码，但不会检查该技能是否可用。通常在[[CanActivateAbility]]检查 及 执行 技能之间需要某些逻辑时才会调用该函数。
		  logseq.order-list-type:: number
		  id:: 653e60d1-28d1-4716-990a-93ae7008ea8d
		- 与Actor和组件不同，玩法技能不会使用[[tick]]函数完成主要工作，而是在激活过程中启动[[Ability Task]]，[[异步]]完成大部分工作，然后连接[[Delegate]]（在C++中）以处理这些任务的输出，或者连接节点以输出执行引脚（在蓝图中）。
		  logseq.order-list-type:: number
		- 如果从`Activate`中调用[[CommitAbility]]函数，它将施加 执行技能 的[[cost]]，例如从[[Gameplay Attribute]]中减去资源（例如"魔法值"、"体力值"或游戏系统所用的任何其他资源）和施加[[冷却]]。
		  logseq.order-list-type:: number
		  id:: 653e60d1-14d7-41a2-8c31-2dd1d5f469e2
		- [[CancelAbility]]提供了取消技能的机制，不过 Ability 的`CanBeCanceled`函数可以拒绝请求。与`CommitAbility`不同，该函数可供**技能外调用者**使用。
		  logseq.order-list-type:: number
		  成功的取消先[[广播]]`On Gameplay Ability Cancelled`，然后通过标准代码路径 结束技能 ，让技能可运行特殊的 清理代码 ，或者其他的 将与 *自行结束* 时的行为不同的 取消时的行为。
		- [[TryActivateAbility]]是执行技能的典型方式。该函数调用[[CanActivateAbility]]来确定技能是否可以立即运行，如果可以，则继续调用[[CallActivateAbility]]。
		  logseq.order-list-type:: number
		- [[EndAbility]]会在技能执行完毕后将其关闭。
		  logseq.order-list-type:: number
		  id:: 653e60d1-378e-461c-a476-fb62e84dae94
		  如果技能被取消，`UGameplayAbility` 类会作为取消流程的一部分自动调用[[EndAbility]]，但其他情况下，开发者都必须调用C++函数或在技能的蓝图图表中添加节点。
		  如果**未能正常结束技能**，将导致玩法技能系统**认为技能仍在运行**，从而带来一些影响，例如禁止将来再使用该技能或任何被该技能阻止的技能。
		  >例如，如果游戏的"喝生命药剂"玩法技能没有正常结束，那么使用该技能的角色就无法执行任何在喝血量药剂时无法执行的操作（例如喝其他药剂、快跑、爬梯子等）。这种阻碍会一直存在，因为玩法技能系统会认为角色还在喝药剂。
- # 复制
	- [[Gameplay Ability]]支持[[internal state]]和[[Gameplay Event]]的[[复制]]，或 关闭复制 以节省 网络带宽 和缩短 CPU周期。
	  id:: 653eb72e-c16e-4d2c-8dcf-cd03faab4190
	  collapsed:: true
	  [[Ability]]的[[Gameplay Ability Replication Policy]]可以设置为`Yes`或`No`，这控制着 Ability 是否[[复制]]自身 *实例*、*更新状态*（update state）或 跨网络发送[[Gameplay Event]]。
	  对于支持 *复制* *技能* 的多人游戏，有几种处理[[复制]]的选项，称为[[Gameplay Net Execution Policy]]：
		- 本地预测（[[Local Predicted]]）：此选项有助于在 *响应能力* 和 *准确性* 之间实现良好的**平衡**。
		  在[[本地客户端]]发出命令后，[[Ability]]将立即在 客户端 上运行，但[[服务器]]起着决定性作用，并且可以根据 Ability 的实际影响来 *覆盖* 客户端。
		  客户端 实际上是从 服务器 请求执行 Ability 的权限，但也在本地进行处理，就好像 服务器 预计会与 客户端 的结果一致。因为客户端在[[本地预测]] Ability 的行为，所以只要 客户端 的 *预测* 与 服务器 不矛盾，它就会非常流畅地运行且 无滞后。
		- 仅限本地（[[Local Only]]）：客户端 仅在 本地 运行技能。如果使用 服务器 的 客户端 是[[主机]]（在物理服务器计算机上玩）或者是在单人游戏中，尽管技能将在服务器上运行，也不会对服务器应用复制。这种情况不适用于专用服务器游戏，因为在专用服务器游戏中客户端永远不会在服务器计算机上运行。客户端通过该技能带来的任何影响都将继续遵循常规复制协议，包括可能从服务器接收更正。
		- 服务器启动：（Server Initiated:）**在服务器上启动的技能将传播到客户端。从客户端的角度来看，这可以更准确地复制服务器上实际发生的情况，但使用技能的客户端会因缺少本地预测而发生延迟。虽然这种延迟非常短，但某些类型的技能（特别是在压力情况下快速执行的操作）将不会像在本地预测模式中那样顺畅。
		- 仅限服务器：（Server Only:）**"仅限服务器"技能将在服务器上运行，不会复制到客户端。被这些技能修改的任何变量都将像往常一样进行复制，这意味着该技能能够影响服务器的权威数据，并会将影响传递给客户端。以这种方式，技能仍然可以影响客户端的观察，尽管技能本身只在服务器上运行。
-