alias:: 网络复制, network replication, replication

- [[服务器]]同步数据和过程调用到[[客户端]]的过程被称为^^复制（Replication）^^ 。
- 服务器和所有客户端生成的actor的 name 编号都可能是不一样的。因为本质上都是各生成各的，没有两个是相同的。
- 角色复制是一个详细的多步骤过程，其中 [[Network Drive]] 决定
	- 哪些 Actor 
	  logseq.order-list-type:: number
	- 需要以何种顺序
	  logseq.order-list-type:: number
	- 复制到哪些[[connection]]。
	  logseq.order-list-type:: number
- 大部分的 Actor 复制发生在 [[UNetDriver::ServerReplicateActors]] 函数中。这是服务器首先为每个客户端收集所有已确定与客户端相关的 Actors ，然后发送自上次更新以来已更改的任何属性的地方。然后，[[UActorChannel::ReplicateActor]] 函数处理特定 [[channel]] 的 Actor 复制的细节。
- ### Actor 复制流程概览
	- 确定哪些 Actors 正在复制，并执行检查以确定^^[[休眠]]状态^^、^^更新频率^^和 [[owning connection]] 。
	  logseq.order-list-type:: number
		- 将通过这些检查的 Actors 添加到^^待考虑复制的列表^^中。
	- 循环遍历每个 [[connection]] ，并根据当前 Actor 和连接执行检查。在这一步结束时，有一个^^为每个 connection 考虑复制的 Actors 列表^^。
	  logseq.order-list-type:: number
		- 按优先级对每个连接的 Actors 进行排序。
	- 确定 Actor 对这个连接是否[[相关]]。
	  logseq.order-list-type:: number
	- 将 Actor 复制到当前 connection 。
	  logseq.order-list-type:: number