alias:: 流送关卡

- 流送关卡通过 [**Levels** 窗口](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/managing-multiple-levels-in-unreal-engine) 进行管理。它可与[[持久关卡]]重叠，或偏移创建更大的世界场景。 使用流送关卡的流送类型可设为 **Always Loaded** 或 **Blueprint**。
	- 流送关卡被设为 **Always Loaded**，它将与持久关卡一同加载。也将和持久关卡同时变为**可见状态**。 它将无视指定的流送体积域，以及来自蓝图或 C++ 的所有加载/卸载请求，除非游戏变更[[持久关卡]]。
		- 这类关卡分段常用于将持久关卡中的常见内容拆分为多个"层"，以便美术师同时协作工作而不会相互阻碍。
- ## [[Level Streaming Volume]]