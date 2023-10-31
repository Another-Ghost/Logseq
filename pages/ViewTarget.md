alias:: FTViewTarget, ViewTarget结构体

- [[ViewTarget结构体]]在[[PlayerCameraManager]]中定义，负责向 PlayerCameraManager 提供理想的[[视角]]。ViewTarget 包含有关 `target Actor`、 `target Actor` 的[[Controller]]（用于[[non-locally controlled Pawn]]），以及[[PlayerState]]的信息（后者用于在[[观战]]时 通过[[Pawn]]的转换和其他变化 来跟踪相同的[[玩家]] #confusing ）。
- *摄像机信息* 被通过[[POV property]]以[[FMinimalViewInfo]]结构体的形式传给[[PlayerCameraManager]]。
  id:: 654131e1-467e-41af-91c5-7aa13aef3290
  `FMinimalViewInfo` 结构包含来自[[CameraComponent]]的 *基本摄像机信息* ，包括  `Location`、`Rotation`、 `Projection Mode`（透视 或 正交）、[[FOV]]、`Orthographic Width`（投影宽度）、[[Aspect Ratio]] 和 [[Post Process Effects]]。向 PlayerCameraManager 提供这些值的访问权限允许其在相机管理过程中在**两种** 相机模式 之间进行[[混合]]。
-