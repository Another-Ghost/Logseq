- 这是所有[[GameMode]]的基类，是经典 [[AGameMode]] 的简化和优化版本。
- AGameModeBase 是新代码项目中包含的新默认游戏模式，因其简单和高效而受到推崇。
- ## 说明
	- `AGameModeBase` 包含大量可重写的基础功能。部分常见函数包括：
	  | 功能/事件 | 用途 |
	  | --- | --- |
	  | `InitGame` | `InitGame`事件在其他任何脚本（包括包括自身的所有`AActor::PreInitializeComponents()`）之前调用，由`AGameModeBase`用来初始化参数和生成其 helper class 。|
	  | `PreLogin` | 接受或拒绝尝试**加入服务器的玩家**。如果设置`ErrorMessage`为非空字符串，则会导致`Login`函数失败。`PreLogin`在`Login`之前调用，尤其是如果加入的玩家需要下载游戏内容，可能在`Login`调用前会有需要大量时间。|
	  | `PostLogin` | 在成功登录后调用。这是首个在 [[PlayerController]] 上安全调用[[replicated function]] 之处。`OnPostLogin`可以在 `Blueprint` 中实现以添加额外逻辑。|
	  | `HandleStartingNewPlayer` | 在 `PostLogin` 后或 [[seamless travel]] 后调用，可以在Blueprint 中重写以改变对**新玩家**的处理方式。默认情况下，它将为玩家创建一个[[pawn]]。|
	  | `RestartPlayer` | 这是开始生成玩家的 [[Pawn]] 的调用。如果你想指定`Pawn`**生成的位置**，还有`RestartPlayerAtPlayerStart`和`RestartPlayerAtTransform`函数可用。`OnRestartPlayer`可以在Blueprint中实现以在此函数完成后添加逻辑。|
	  | `SpawnDefaultPawnAtTransform` | 这是实际生成玩家的 [[Pawn]] 的函数，可以在Blueprints中被重写。|
	  | `Logout` | 当**玩家离开游戏或被销毁时**调用。`OnLogout`可以实现以执行Blueprint逻辑。|
	-