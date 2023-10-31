alias:: 摄像机

- [[Camera]]代表了玩家的视角。因此， 摄像机只和玩家控制的人物有关。[[PlayerController]]会指定一个 Camera 类， 并实例化一个[[CameraActor]]，以此计算玩家从哪个 位置 和 角度 观察世界。
- 摄像机 可以添加[[后期处理效果]]。
- 游戏特定的摄像机行为和摄像机可以随时通过 "责任链" 提供（从上到下通过以下类传递，然后转到 `ALocalPlayer`，并以[渲染](https://docs.unrealengine.com/5.3/zh-CN/designing-visuals-rendering-and-graphics-with-unreal-engine), **场景视图（Scene View）** (`FSceneView`) 以及其它相关系统结束）。