alias:: Actor/PlayerCameraManager

- [[PlayerCameraManager]]用于为一个特定的[[player]]管理[[camera]]。
  它定义最终查看属性，供渲染器这类的其它系统使用。PlayerCameraManager的功能类似于一个用来查看世界的 "虚拟眼球"。 它可以直接计算最终摄像机属性，也能够在其它物体或者影响摄像机的Actor之间混合（从一个CameraActor混合到另外一个）。
- PlayerCameraManager的主要外部职责是要可靠地对各种 `Get()` 函数做出响应，比如 `GetCameraViewPoint`。 默认情况下，PlayerCameraManager保留一个查看目标，为摄像机所关联的主要Actor。它可以向最终查看状态应用各种后期效果，比如摄像机动画、后期处理效果或者特殊效果（比如摄像机镜头上的尘土）。
- 如果你需要从PlayerCameraManager继承，并且你是创建一个父类蓝图而不是C++，那么PlayerCameraManager会包含 `BlueprintUpdateCamera` 函数来实现你自己的自定义摄像机。