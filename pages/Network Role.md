- Actor的[[network role]]将决定网络游戏期间控制Actor的 *机器* 。[[authoritative Actor]]被认为可控制Actor的**状态**，并可将信息[[复制]]到网络多人游戏会话中的其他机器上。[[remote proxy]]是该Actor在远程机器上的副本，其将**接收** *权威Actor* 中的复制信息。其由[[Local Role]]和[[Remote Role]]变量进行追踪，它们可取以下值：
  id:: 653c9e42-4269-4a9e-80f4-2a861c1e192c
- id:: 653ca431-e012-4278-884c-17c2c2cffe05
  |Network Role|说明|
  |--|--|
  |None|Actor**在网络游戏中无角色**，**不会复制**。|
  |[[Authority]]|Actor为[[authoritative]]状态，会将其信息复制到其他机器上的[[远程代理]]。|
  |[[Simulated Proxy]]|Actor为[[远程代理]]，由另一台机器上的[[Actor完全控制。网络游戏中如拾取物、发射物或交互对象等多数Actor将在远程客户端上显示为模拟代理。|
  |Autonomous Proxy|Actor为远程代理，能够本地执行部分功能，但会接收授权Actor中的矫正。自主代理通常为玩家直接控制的actor所保留，如pawn。|
-