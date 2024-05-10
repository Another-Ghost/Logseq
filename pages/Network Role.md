- Actor的[[network role]]将决定网络游戏期间控制Actor的 *机器* 。[[authoritative Actor]]被认为可控制Actor的**状态**，并可将信息[[复制]]到网络多人游戏会话中的其他机器上。[[remote proxy]]是该Actor在远程机器上的副本，其将**接收** *权威Actor* 中的复制信息。其由[[Local Role]]和[[Remote Role]]变量进行追踪，它们可取以下值：
  id:: 653c9e42-4269-4a9e-80f4-2a861c1e192c
- id:: 653ca431-e012-4278-884c-17c2c2cffe05
  |Network Role|说明|
  |--|--|
  |None|Actor**在网络游戏中无角色**，**不会复制**。|
  |[[Authority]]|Actor为[[authoritative]]状态，会将其信息复制到其他机器上的[[远程代理]]。|
  |[[Simulated Proxy]]|Actor为[[远程代理]]，由另一台机器上的[[authoritative Actor]]完全控制。网络游戏中如 *拾取物* 、*发射物* 或 *交互对象* 等多数Actor将在[[远程客户端]]上显示为模拟代理。|
  |[[Autonomous Proxy]]|Actor为[[远程代理]]，能够**本地执行 部分功能**，但会接收[[authoritative Actor]]中的矫正。自主代理通常为**玩家直接控制的actor**所保留，如[[Pawn]]。|
- 虚幻引擎使用的默认模型是[[server-authoritative]]，意味着服务器对游戏状态具有权威性，而信息固定从服务器复制到客户端。服务器上的Actor为具有[[Authority]]的[[Local Role]]，而其在远程客户端上的对应Actor应具有[[Simulated Proxy]]或[[Autonomous Proxy]]的本地角色。
- 欲了解Actor网络角色，参见[Actor角色和远程角色](https://docs.unrealengine.com/5.3/zh-CN/actor-role-and-remoterole-in-unreal-engine)指南。