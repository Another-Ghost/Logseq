alias:: Actor/PlayerCameraManager

- [[PlayerCameraManager]]用于为一个特定的[[player]]管理[[camera]]。
  它定义最终 view 属性，供[[Renderer]]这类的其它系统使用。
- >PlayerCameraManager 的功能类似于一个用来查看世界的 "虚拟眼球"。
- 它可以直接计算 最终摄像机属性 ，也能够在其它影响[[摄像机]]的 Object 或 Actor 之间混合（从一个[[CameraActor]]混合到另外一个）。
- PlayerCameraManager 的主要外部职责是要可靠地对各种 `Get()` 函数做出响应，比如 `GetCameraViewPoint`。
  默认情况下，PlayerCameraManager保留一个[[ViewTarget]](为摄像机所关联的主要 Actor )。
  它可以向最终 view state 应用各种[[后期效果]]，比如[[camera animation]]、[[后期处理效果]]或者 *特殊效果*（比如摄像机镜头上的尘土）。
- 如果你需要从 PlayerCameraManager 继承，并且你是创建一个父类蓝图而不是C++，那么PlayerCameraManager 会包含 `BlueprintUpdateCamera` 函数来实现你自己的自定义摄像机。
-