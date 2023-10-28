alias:: 相关性

- **相关性** 用于决定是否需要在多人游戏期间复制Actor。复制期间将剔除被认为不相关的actor。此操作可节约带宽，以便相关Actor可更加高效地复制。若Actor未被玩家拥有，且不在玩家附近，将其被视为不相关，而不会进行复制。不相关Actor会存在于服务器上，且会影响授权游戏状态，但在玩家靠近前不会向客户端发送信息。覆盖 `IsNetRelevantFor` 函数以手动控制相关性，并可使用 `NetCullDistanceSquared` 属性决定成为相关Actor所需距离。
- 有时在游戏单帧内，没有足够带宽供复制所有相关Actor。因此，Actor拥有 **优先级（Priority）** 值，用于决定优先复制的Actor。Pawn和PlayerController的 `NetPriority` 默认为 **3.0**，从而使其成为游戏中最高优先级的Actor，而基础Actor的 `NetPriority` 为 **1.0**。Actor在被复制前经历的时间越久，每次成功通过时所处的优先级便越高。
- 欲了解Actor相关性和优先级的详情，参见[网络优先级](https://docs.unrealengine.com/5.3/zh-CN/actor-relevancy-and-priority-in-unreal-engine)上的指南。