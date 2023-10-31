alias:: FTViewTarget, ViewTarget结构体

- [[ViewTarget结构体]]在[[PlayerCameraManager]]中定义，负责向 PlayerCameraManager 提供理想的[[视角]]。ViewTarget 包含有关 `target Actor`、 `target Actor` 的[[Controller]]（用于[[non-locally controlled Pawn]]），以及[[PlayerState]]的信息（后者用于在[[观战]]时 通过[[Pawn]]的转换和其他变化 来跟踪相同的[[玩家]] ）。
- 摄像机信息被通过视角（POV）属性以 "FMinimalViewInfo" 结构体的形式传给PlayerCameraManager。该结构包含来自 CameraComponent 的基本摄像机信息，包括 **位置（Location）**、**旋转（Rotation）**、 **投射模式（Projection Mode）**（透视或正交）、**视场（FOV）**、**投影宽度（Orthographic Width）**、**宽高比（Aspect Ratio）** 和 **后期处理效果（Post Process Effects）**。让 PlayerCameraManager访问这些值使PlayerCameraManager能在 摄像机管理期间混合两种摄像机模式。
-