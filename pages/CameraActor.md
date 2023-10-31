alias:: Actor/CameraActor, ACameraActor

- 有关[[摄像机]]的所有 *属性* 和 *行为* 均在[[CameraComponent]]中设置。[[CameraActor]]类主要用作[[CameraComponent]]的 wrapper，以使 Camera 可以被直接放置在关卡内，而非另一个类中。
  id:: 65410e90-517a-494f-acd8-c6a697b9ac0f
- 两个 组件 被添加到[[CameraComponent]]，以辅助编辑器中的可视化布置，不过它们在游戏期间将 不可见 。
	- [[FrustumComponent]]显示 摄像机的[[FOV]]位置。
-