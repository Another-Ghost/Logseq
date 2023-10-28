alias:: RPCs, Remote Procedure Calls, 远程过程调用, replicated function, replicated functions

- [[远程过程调用]]可以从任何机器上调用，但将其实际执行定向到连接到网络会话的特定机器上。有三种类型的RPC可用：
  |RPC类型|说明|
  |--|--|
  |[[Server]]|仅在主持游戏的[[服务器]]上调用。|
  |[[Client]]|仅在拥有 该函数所属Actor 的[[客户端]]上调用。若Actor没有连接，将不会执行此逻辑。|
  |[[NetMulticast]]|在与服务器连接的**所有**[[客户端]]及[[服务器]]本身上调用。|