alias:: Gameplay Framework/Gameplay Timer, Timer, 定时器

- 定时器在**全局定时器管理器**（[[FTimerManager]]类型）中管理。
- 如果要对调用定时器的对象（如 Actor ）在定时结束前被销毁，则相关定时器会**自动取消**。在此情况下，[[timer handle]] 将变为无效，并且不会调用该函数。
- Gameplay Timer可以与 C++[[函数指针]], [[TFunction]]或[[Delegate]]一起使用。
- ## 说明
- ### 设置定时器
	- 定时器还可以设置为在下一帧运行，而不是按固定间隔。实现方法是调用 `SetTimerForNextTick`，但需要注意的是，该函数不填充定时器句柄。
- ### 问题
	- 该代码目前并非[[线程安全]]，如果从[[游戏线程]]外部访问可能会导致断言。
- ## Reference
	- https://dev.epicgames.com/documentation/zh-cn/unreal-engine/gameplay-timers-in-unreal-engine