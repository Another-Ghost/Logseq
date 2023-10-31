alias:: Component/CameraComponent

- [[CameraComponent]]代表[[摄像机]] 视角 和 设置 ，比如 [[Projection]] Type 、[[Field Of View]] 和 [[Post-Process]] Overrides 。
- ## ViewTarget
	- [[ViewTarget]]是一个[[CameraActor]]或者包含[[CameraComponent]]并且 `bFindCameraComponentWhenViewTarget` 设为 `true` 的[[Actor]]。
	- `bTakeCameraControlWhenPossessed` 是一个任何[[Pawn]]可以设置的相关属性，Pawn 会在[[PlayerController]][[Possess]]时自动变为[[ViewTarget]]。
- ## Actor 和 PlayerController
	- [[Actor]]都含有[[CalcCamera]]函数。
	  如果 `bFindCameraComponentWhenViewTarget` 为 `true`，而且[[CameraComponent]]存在，[[Actor]]的 `CalcCamera` 函数返回 Actor中的首个 CameraComponent 的[[camera view]]。
	  否则，`CalcCamera`获取 Actor 的 位置 和 旋转方向 。
	- 在[[PlayerController]]类中，[[CalcCamera]]函数的行为方式与第二种情况类似，如果存在 possessed Pawn ，则返回 Pawn 的位置以及 PlayerController 的[[control rotation]]。
-