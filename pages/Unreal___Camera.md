alias:: 摄像机

- [[Camera]]代表了玩家的视角。因此， 摄像机只和玩家控制的人物有关。[[PlayerController]]会指定一个 Camera 类， 并实例化一个[[CameraActor]]，以此计算玩家从哪个 位置 和 角度 观察世界。