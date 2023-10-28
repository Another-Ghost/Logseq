alias:: Actor复制, 复制Actor, replicated Actor

- [[复制]]是指在[[网络会话]]中的不同机器间复制**游戏状态信息**。若正确设置复制，将可同步不同机器的游戏实例。多数Actor默认不会启用复制，且将本地执行所有功能。在[[Actor]]类中设置 `bReplicates` 变量，可启用给定类的Actor复制。
- id:: 653c957a-6323-403d-b63c-ca1068d62cca
  |复制功能|说明|
  |--|--|
  |[[创建]]和[[销毁]]| *服务器* 上生成 *复制的Actor* 的[[权威]]版本时，其会在所有连接 *客户端* 上自动生成[[远程代理]]。其之后会将信息复制到这些远程代理。若销毁权威Actor，则将自动销毁所有连接客户端上的远程代理。|
  |[[移动复制]]|若授权Actor启用了 [[Replicate Movement]]，其将**自动复制**位置、旋转和速度。|
  |[[变量复制]]|在指定为复制变量的**值变更时**，其将**自动**从授权Actor复制到其远程代理。|
  |[[组件复制]]|Actor组件复制为其所属Actor的一部分。组件内指定为复制变量将复制，而组件内调用的[[RPC]]将与Actor类中调用的RPC保持**一致**。|
  |[[远程过程调用]]（RPC）|RPC是传输到网络游戏中特定机器的特殊函数。无论初始调用RPC的是哪台机器，其实现**仅在目标机器上运行**。|
- 虽然**创建、销毁和移动等常见使用可自动处理**，但即使启用复制，**其他所有gameplay功能也不会默认自动复制**。必须根据游戏的需求**明确指定要复制的变量和函数**。欲了解上述所有复制功能的详情，参见[[属性复制]]指南。
  id:: 653c9b5d-9e4e-49eb-b8c5-b4b1a644c83d
- Actor、Pawn和角色的部分常用功能不会复制：
	- [[骨架网格体]]和[[静态网格体]]组件
	- [[材质]]
	- [[动画蓝图]]
	- [[粒子系统]]
	- [[音效发射器]]
	- [[Physics Object]]
- 此类项目均在**所有客户端上单独运行**。但是，若复制**驱动此类视觉元素的变量**，则可确保所有客户端都具有相同信息，从而以**大致相同的方式进行模拟**。
- ## 创建Replicated Actor的核对清单
	- 按照以下步骤，可创建[[replicated Actor]]：
		- 将Actor的`Replicated setting`设为True。
		  logseq.order-list-type:: number
		- 若复制Actor需要 移动，将[[Replicates Movement]]设为`True`。
		  logseq.order-list-type:: number
		- 生成 或 销毁 replicated Actor 时，确保**在服务器上执行该操作**。
		  logseq.order-list-type:: number
		- 设置必须在机器间**共享**的 变量，以便进行复制。这通常适用于核心的gameplay变量。
		  logseq.order-list-type:: number
		- 尽量使用虚幻引擎的 *预制*[[移动组件]]，其已针对复制进行构建。
		  logseq.order-list-type:: number
		- 若使用[[server-authoritative]]模型，需确保玩家可执行的新操作均由[[服务器函数]]触发。
		  logseq.order-list-type:: number