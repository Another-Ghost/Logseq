alias:: Component/CameraComponent

- [[CameraComponent]]代表[[摄像机]] 视角 和 设置 ，比如 [[Projection]] Type 、[[Field Of View]] 和 [[Post-Process]] Overrides 。如果ViewTarget是一个CameraActor或者包含CameraComponent并且 `bFindCameraComponentWhenViewTarget` 设为 *true* 的 Actor 。`bTakeCameraControlWhenPossessed` 是一个可以为任何Pawn设置的相关属性，Pawn会在PlayerController占有时自动变为ViewTarget。
-