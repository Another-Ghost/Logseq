alias:: 游戏模式, GameMode, game mode

- ^^GameMode^^ 是指定在 [[Gameplay Framework]] 中使用哪些其他类的主要类，管理 gameplay session 的总体规则和结构。
	- 如^^比赛格式^^、^^任务类型^^或地图^^特殊区域^^等
-
- ### 网络
  Game Mode **不会复制到加入多人游戏的任何[[远程客户端]]**；它**只存在于[[服务器]]**上。
	- 如果玩家确实需要 与当前Game Mode 相关的更新信息，这些信息可以通过存储在 [[AGameStateBase]] 上来保持同步。
- ### 创建
  Game mode是关卡加载并创建世界后**首先实例化**的 actor，每次^^level 初始化^^时都会通过[[UGameEngine::LoadMap()]] 实例化一个 Game Mode Actor。
	- 由于此类是在关卡加载时创建的，它不会跨关卡存在，并可以按地图设置。也就是任何给定时间只能使用一个 game mode 。
	- 在 GameMode 创建时实例化其余的 framework 中的 actors。前两个是[[game state]]和[[player state]]。
- ### 类型
  目前有两个常用的 GameMode 基类：
	- [[AGameModeBase]]
	  logseq.order-list-type:: number
	- [[AGameMode]]
	  logseq.order-list-type:: number
- 派生自 Game Mode 的蓝图可进行以下默认设置：
	- 默认 [[Pawn]] 类
	- [[HUD]] 类
	- [玩家控制器](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/player-controllers-in-unreal-engine) 类
	- Spectator 类
	- Game State 类
	- Player State 类