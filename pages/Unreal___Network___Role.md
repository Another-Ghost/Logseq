alias:: Role, network role, AActor::Role

- 在 Actor 的复制过程中，有两个重要属性： [[Role]] 和 [[RemoteRole]]。
  有了这两个属性，您可以知道：
	- 谁拥有 actor 的 [[authority]]
	- actor 是否被[复制]([[Actor复制]])
	- Actor 的复制模式（[[replication role]]）
- ### [[Authority]]
- ## 复制模式
  服务器不会在每次更新时复制 actor。这会消耗太多的带宽和 CPU 资源。实际上，服务器会按照 `AActor::NetUpdateFrequency` 属性指定的频度来复制 actor。
  因此在 actor 更新的间歇，会有一些时间数据被传递到客户端。这会导致 actor 呈现出断续、不连贯的移动。为了弥补这个缺陷，客户端将在更新的间歇中模拟 actor。
  目前共有两种类型的模拟。
- ### `ROLE_SimulatedProxy`
  
  这是标准的模拟途径，通常是根据上次获得的速率对移动进行推算。当服务器为特定的 actor 发送更新时，客户端将向着新的方位调整其位置，然后利用更新的间歇，根据由服务器发送的最近的速率值来继续移动 actor。
  
  使用上次获得的速率值进行模拟，只是普通模拟方式中的一种。您完全可以编写自己的定制代码，在服务器更新的间隔使用其他的一些信息来进行推算。
- ### `ROLE_AutonomousProxy`
  
  这种模拟通常只用于 PlayerController 所拥有的 actor。这说明此 actor 会接收来自真人控制者的输入，所以在我们进行推算时，我们会有更多一些的信息，而且能使用真人输入内容来补足缺失的信息（而不是根据上次获得的速率来进行推算）。
-
- Actor的[[Role]]将决定网络游戏期间控制Actor的机器。
	- [[authoritative Actor]]被认为可控制Actor的**状态**，并可将信息[[复制]]到网络多人游戏会话中的其他机器上。
	  logseq.order-list-type:: number
	- [[remote proxy]]是该Actor在远程机器上的副本，其将**接收** *权威Actor* 中的复制信息。其由[[Local Role]]和[[Remote Role]]变量进行追踪。
	  logseq.order-list-type:: number
- 它们可取以下值：
  |Network Role|说明|
  |--|--|
  |None|Actor**在网络游戏中无角色**，**不会复制**。|
  |[[Authority]]|Actor为[[authoritative]]状态，会将其信息复制到其他机器上的[[远程代理]]。|
  |[[Simulated Proxy]]|Actor为[[远程代理]]，由另一台机器上的[[authoritative Actor]]完全控制。网络游戏中如 *拾取物* 、*发射物* 或 *交互对象* 等多数Actor将在[[远程客户端]]上显示为模拟代理。当前客户端中的**其他玩家** 的 Role 为 Simulated Proxy|
  |[[Autonomous Proxy]]|Actor为[[远程代理]]，能够**本地执行 部分功能**，但会接收[[authoritative Actor]]中的矫正。自主代理通常为**玩家直接控制的actor**所保留，如[[Pawn]]。|
- 虚幻引擎使用的默认模型是[[server-authoritative]]，意味着服务器对游戏状态具有权威性，而信息固定从服务器复制到客户端。服务器上的Actor为具有[[Unreal/Network/Authority]]的[[Local Role]]，而其在远程客户端上的对应Actor应具有[[Simulated Proxy]]或[[Autonomous Proxy]]的本地角色。
-
- 要确定当前运行的引擎实例是否有主控者，需要查看 Role 属性是否为 `ROLE_Authority`。如果是，就表明这个运行中的 **虚幻引擎** 实例负责掌管此 actor
- id:: 6643b2f5-3c5d-4846-af41-6c2480c19aa2