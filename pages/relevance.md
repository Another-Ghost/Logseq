alias:: 相关性, 相关actor

- [[相关性]]用于决定是否需要在多人游戏期间复制Actor。复制期间将**剔除被认为[[不相关]]的actor**。此操作可节约[[带宽]]，以便相关Actor可更加高效地复制。
  id:: 653cac3e-b3ed-487a-8386-4bd75d04eba2
  若Actor未被玩家[[拥有]]，且**不在玩家附近**，将其被视为[[不相关]]，而不会进行复制。
  [[不相关Actor]]会存在于 *服务器* 上，且会影响[[authoritative]][[game state]]，但在玩家靠近前不会向客户端发送信息。重写 `IsNetRelevantFor` 函数以手动控制相关性，并可使用 `NetCullDistanceSquared` 属性决定成为 *相关Actor* 所需 *距离* 。