alias:: AActor UObject/Actor

- ^^Actor^^是可以在[[关卡]]中放置或生成的对象的基类。
	- Actor 支持 [transformation]([[Unreal]])。
	  logseq.order-list-type:: number
	- Actor可以包含一系列[[ActorComponent]]。
	  logseq.order-list-type:: number
	- Actor 支持[网络复制属性]([[Unreal/Network/Actor Replication]])和函数调用。
	  logseq.order-list-type:: number
- ## 生命周期
  id:: 663dcee1-b1c0-4be5-8e5d-115f6eb5fef7
	- ### [[Load From Disk]]
	  ^^从磁盘加载（Load From Disk）^^路径适用于已经在 [[Level]] 中的 Actor 。
	  如当 `UEngine::LoadMap` 发生时，或当[[关卡流送]]调用 `UWorld::AddToWorld` 时。
		- 从磁盘加载 [[Package]] /[[Level]]中的 Actor （到内存中）。
		  logseq.order-list-type:: number
		- 序列化的Actor 从磁盘加载完成后调用 [[AActor::PostLoad]] 。
		  logseq.order-list-type:: number
			- 所有**自定义版本化和修复操作**应在此处执行。
			  logseq.order-list-type:: number
			- logseq.order-list-type:: number
			  [[AActor::PostLoad]]与[[AActor::PostActorCreated]]互斥。
		- logseq.order-list-type:: number
		  世界调用[UAISystemBase::InitializeActorsForPlay](https://dev.epicgames.com/documentation/404)，以为 Actor 启动gameplay 做准备。
		- 关卡为**未初始化的 Actor** 和 **[[seamless travel]] 中的 [[persisting actor]]** 调用 [[ULevel::RouteActorInitialize]] ：
		  logseq.order-list-type:: number
			- 在 Actor 的[[component]]上调用 [[UActorComponent::InitializeComponent]] 之前调用[[AActor::PreInitializeComponents]]。
			  logseq.order-list-type:: number
			- logseq.order-list-type:: number
			  [[UActorComponent::InitializeComponent]]是 Actor 上定义的每个组件的创建辅助函数。
			- logseq.order-list-type:: number
			  在Actor的组件初始化后，调用[[AActor::PostInitializeComponents]]。
		- logseq.order-list-type:: number
		  **关卡启动后**，调用[[AActor::BeginPlay]]。
	- ### [[Play in Editor]]
	  在^^在编辑器中运行（Play in Editor）^^路径中，Actor 通过**将编辑器中的 Actor 复制到新 world 中**的方式生成，并非从磁盘中加载。
	  然后，复制的Actor按与[[从磁盘加载]]路径中所述的相同流程初始化。
	- ### [Spawning]([[spawn Actor]])
	  当你^^生成^^ Actor 的实例时，这是相关路径：
		- logseq.order-list-type:: number
		  调用[[UWorld::SpawnActor]]。
		- 在世界中生成 Actor 后，调用 [[AActor::PostSpawnInitialize]] .
		  logseq.order-list-type:: number
		- spawnedActor 创建后为其调用 [[AActor::PostActorCreated]] ,所有构造函数实现行为应在此发生。
		  logseq.order-list-type:: number
			- PostActorCreated 与 [[AActor::PostLoad]] 互斥。
			  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  [[AActor::ExecuteConstruction]]
		- logseq.order-list-type:: number
		  [[AActor::OnConstruction]]是 Actor 的 construction 函数，[Blueprint Actor 的 component]([[Blueprint Actor Component]]) 在此处创建，[[蓝图变量]]在此处初始化。
		- [[AActor:PostActorConstruction]]：
		  logseq.order-list-type:: number
			- 在 Actor 的[[component]]上调用 [[UActorComponent::InitializeComponent]] 之前调用[[AActor::PreInitializeComponents]]。
			  logseq.order-list-type:: number
			- logseq.order-list-type:: number
			  [[UActorComponent::InitializeComponent]]是 Actor 上定义的每个组件的创建辅助函数。
			- logseq.order-list-type:: number
			  在Actor的组件初始化后，调用[[AActor::PostInitializeComponents]]。
		- UWorld 上会 broadcast  [[UWorld::OnActorSpawned]] 。
		  logseq.order-list-type:: number
		- 调用 [[AActor::BeginPlay]] 。
		  logseq.order-list-type:: number
	- ### Deferred Spawn
	  将 Actor 的任意属性设为^^生成时公开（[[Expose on Spawn]]）^^即可导致^^延迟生成^^ Actor 。
		- [[UWorld:SpawnActorDeferred]] 旨在生成[[procedural Actor]] , 允许在 [[Blueprint construction script]] 之前进行额外设置。
		  logseq.order-list-type:: number
		- 之后会执行[[Spawn Actor]]中的所有操作，但在[[AActor::PostActorCreated]]之后发生以下操作：
		  logseq.order-list-type:: number
			- 通过一个有效但不完整的 ^^Actor instance^^ 设置并调用多个 initialization function 。
			  logseq.order-list-type:: number
			- logseq.order-list-type:: number
			  调用[[AActor::FinishSpawning]] ，以完成生成 Actor 。
				- logseq.order-list-type:: number
				  [[AActor::ExecuteConstruction]] 之后的步骤和[[Spawn Actor]]一致。
	- ## End of Actor Lifecycle
		- 当游戏在任何时候需要移除 Actor 时，手动调用[[AActor::Destroy]]，但 Gameplay 仍在继续。Actor 被标记为 [[pending kill]] 并从关卡的 Actor 数组中移除。
		- 调用[[EndPlay]]的全部情形：
			- 对 [[AActor::Destroy]] 显式调用。
			- [[Play in Editor]]终结。
			- [[关卡过渡]]（[[无缝切换]]或[[加载地图]]）。
			- 包含Actor的[[streaming level]]被卸载。
			- Actor 的[[life time]]已过。
			- 应用程序关闭（全部Actor被销毁）。
		- 无论这些情形出现的方式如何，Actor都将被标记为 `RF_PendingKill` ，因此在下个垃圾回收周期中，UE会将其从内存中解除分配。此外，可以考虑使用更清晰的[FWeakObjectPtr<AActor>]([[FWeakObjectPtr]]) 代替手动检查是否 pending kill 。
- ## Reference
	- https://dev.epicgames.com/documentation/zh-cn/unreal-engine/unreal-engine-actor-lifecycle
-