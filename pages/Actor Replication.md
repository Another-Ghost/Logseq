alias:: Actor复制

- [[复制]]是指在[[网络会话]]中的不同机器间复制**游戏状态信息。若正确设置复制，将可同步不同机器的游戏实例。多数Actor默认不会启用复制，且将本地执行所有功能。在C++ Actor类中设置 `bReplicates` 变量，或将Actor蓝图的 **复制（Replicates）** 设置设为 **true**，可启用给定类的Actor复制。
-