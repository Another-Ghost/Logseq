- `UActorChannel::ReplicateActor` 是将 Actor 及其所有组件复制到 connection 的主要方法。流程大致如下：
	- 确定这是否是自此 Actor 通道打开以来的第一次更新。
	  logseq.order-list-type:: number
		- 如果是，则[[序列化]]所需的特定信息（初始位置、旋转等）。
		  logseq.order-list-type:: number
	- 确定此[[连接]]是否拥有此 Actor。
	  logseq.order-list-type:: number
		- 如果未拥有，并且此 Actor 的 [[role]] 为 [[ENetRole::ROLE_AutonomousProxy]]，则降级为 [[ENetRole::ROLE_SimulatedProxy]] 。
		  logseq.order-list-type:: number
		- 复制此 [[Actor]] **更改的属性**。
		  logseq.order-list-type:: number
		- 复制每个 [[Component]] **更改的属性**。
		  logseq.order-list-type:: number
	- 对任何^^已删除的组件^^发送^^特殊删除命令^^。
	  logseq.order-list-type:: number
- 在耗尽 Actors 列表或 [[channel]]饱和 后，考虑下一个 connection ，重复此过程，直到更新所有 connection。
- > 有关 Actor 复制的更多信息，请参阅 Unreal Engine 源代码中的以下头文件：
	- `/Engine/Source/Runtime/Engine/Classes/Engine/NetDriver.h`
	  关于 `UNetDriver::ServerReplicateActors` 的信息。
	- `/Engine/Source/Runtime/Engine/Classes/GameFramework/Actor.h`
	  关于 AActor 及其功能和属性的信息。
	- `/Engine/Source/Runtime/Engine/Classes/Engine/ActorChannel.h`
	  关于 `UActorChannel` 和 `UActorChannel::ReplicateActor` 的信息。
	- `/Engine/Source/Runtime/Engine/Classes/Engine/EngineTypes.h`
	  关于诸如 `ENetRole` 和 `ENetDormancy` 等类型的信息。