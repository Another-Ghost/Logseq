- Game instance 在**引擎启动时**实例化，并保持活动状态直到引擎关闭。
  它是一个管理类，没有实体，用于跟踪数据和运行代码。
- 任何你希望在**[[关卡加载]]之间持续存在**的内容都应该存放在 game instance 中。
	- 例如，这使得 game instance 成为管理你的[[保存游戏系统]]的好地方。
- Game Instance Subsystem
  Game instance 还充当任意数量的 [[game instance subsystem]] 的**管理器**，这些子系统由 game instance 创建和销毁，并且**生存期**与 game instance 本身相同。
	-
- ### 网络
  Game instance **不进行[[网络复制]]**：网络多人游戏中，服务器和所有连接的客户端中都存在独立的 Game Instance。
	-
-