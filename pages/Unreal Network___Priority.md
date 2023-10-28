alias:: Unreal Network/优先级, NetPriority

- 有时在游戏 *单帧* 内，没有足够[[带宽]]供复制所有[[相关Actor]]。因此，Actor拥有[[Priority]]值，用于决定优先复制的Actor。
  [[Pawn]]和[[PlayerController]]的 `NetPriority` 默认为 3.0，从而使其成为游戏中**最高优先级**的Actor，而基础Actor的 `NetPriority` 为 **1.0**。Actor在**被复制前经历的时间越久**，那么它的优先级 *优先级* 便越高，直到它成功进行复制。
- 欲了解Actor相关性和优先级的详情，参见[网络优先级](https://docs.unrealengine.com/5.3/zh-CN/actor-relevancy-and-priority-in-unreal-engine)上的指南。