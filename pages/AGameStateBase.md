- [[AGameStateBase]] 是[[Game Mode]]基础实现，其部分默认功能包括：
  |`GetServerWorldTimeSeconds`|这是 `UWorld` 函数 `GetTimeSeconds` 的**服务器版本**，将在客户端和服务器上同步，因此该时间可用于[[复制]]，十分可靠。 |
  |--|--|
  |`PlayerArray`|这是所有 `APlayerState` 对象的阵列，对游戏中所有玩家执行操作时十分实用。|
  |`HasBegunPlay`|如 `BeginPlay` 函数在游戏中的 actor 上调用，则返回 true。|
-
-