alias:: 网络复制, network replication, replication, Actor Replication

- [[服务器]]同步数据和过程调用到[[客户端]]的过程被称为^^复制（Replication）^^ 。
- 服务器和所有客户端生成的actor的 name 编号都可能是不一样的。因为本质上都是各生成各的，没有两个是相同的。
- ### 重要属性
  |属性 | 描述|
  |--- | ---|
  |`AActor::NetUpdateFrequency` | 决定 Actor 应该多久复制一次。|
  |[[AActor::PreReplication]] | 在任何复制发生之前调用。|
  |[[AActor::bOnlyRelevantToOwner]] | 如果此 Actor 仅复制到其[[owner]]，则为 `true` 。|
  |[[AActor::IsRelevancyOwnerFor]] | 当 [[bOnlyRelevantToOwner]] 为 `true` 时，决定 [[Actor]] 。|
  |[[AActor::IsNetRelevantFor]] | 当 [[bOnlyRelevantToOwner]] 为 `false` 时，决定 [[Actor 相关性]]。|
  |[[AActor::NetDormancy]] | 决定 Actor 是处于休眠状态还是激活状态。|
- 角色复制是一个详细的多步骤过程，其中 [[Network Drive]] 决定
	- 哪些 Actor 
	  logseq.order-list-type:: number
	- 需要以何种 order
	  logseq.order-list-type:: number
	- 复制到哪些[[connection]]。
	  logseq.order-list-type:: number
- 大部分的 Actor 复制发生在 [[UNetDriver::ServerReplicateActors]] 函数中。这是服务器首先为每个客户端收集所有已确定与客户端相关的 Actors ，然后发送自上次更新以来已更改的任何属性的地方。然后，[[UActorunreal::ReplicateActor]] 函数处理特定 [[channel]] 的 Actor 复制的细节。
- ### [[Actor Replication]]流程概览
	- 确定哪些 Actors 正在复制，并执行检查以确定^^[[休眠]]状态^^、^^更新频率^^和 [[owning connection]] 。
	  logseq.order-list-type:: number
		- 将通过这些检查的 Actors 添加到^^待考虑复制的列表^^中。
		- 对于通过这些初步检查的任何 Actor，将调用 `AActor::PreReplication`。在 [[AActor::PreReplication]] 中，你可以决定是否希望属性在某些连接中复制。使用 [[DOREPLIFETIME_ACTIVE_OVERRIDE]] 宏来具体控制 Actor 复制到哪些连接。如果 Actor 通过了上述所有检查，则将其添加到待复制列表中。
	- 循环遍历每个 [[connection]] ，并根据当前 Actor 和连接执行检查。在这一步结束时，有一个^^为每个 connection 考虑复制的 Actors 列表^^。
	  logseq.order-list-type:: number
		- 按优先级（[[AActor::GetNetPriority]]）对每个连接的 Actors 进行排序。
	- 确定 Actor 对这个连接是否[[相关]]。
	  logseq.order-list-type:: number
	- 对于通过上述所有检查的任何 Actor ，将通过调用 [[UActorChannel::ReplicateActor]] 将 Actor 复制到 [[connection]] 。
	  logseq.order-list-type:: number
-
- ## Reference
	- https://dev.epicgames.com/documentation/zh-cn/unreal-engine/detailed-actor-replication-flow-in-unreal-engine