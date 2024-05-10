alias:: level, 关卡

- ^^关卡（Level）^^是游戏的"世界"的全部或一部分。
  关卡包含玩家可以看到并与之交互的所有内容，例如环境、可用对象、其他角色，等等。
- 虚幻引擎将每个关卡保存为单独的 [[.umap]] 文件，所以关卡有时也被称为 [[Map]]  。
- 下面是组合起来创建关卡至少所需的元素列表：
	- 一个 [[.umap]] 文件，即关卡本身。可将其视为保存其他所有内容的**容器**。
	- 一个由 **静态网格体Actor（Static Mesh Actors）** 组成的环境。
		- 这些可以是树木、岩石、墙壁或其他固定装环境装置。某些场景还使用其他类型的Actor，例如地形 Actor 或者水体 Actor 。
	- 一个由 **骨骼网格体Actor（Skeletal Mesh Actor）** 表示的玩家角色。
	- 一个或多个不同类型的[[光源]]（lights） 。
	- [[Ambient sound]] 和[[音效]]（例如，脚步声）。
	- 复杂的关卡可能包含其他功能，如[[粒子特效]]、[[视效后期处理]]、[[Level Streaming]]，等等。
- 引擎中总是会有一个 [[Persistent Level]] ，并且你可以有一个或多个[[子关卡]]，子关卡总是通过[[Level Streaming Volume]] 、 **蓝图（Blueprints）** 或 **C++代码（C++ code）** 加载或[[流送]]。
- ### visibility
  更改关卡的 [[visibility]] 只会影响它的显示，不会对关卡能否加载进游戏产生影响。不过，当你重新生成关卡时，此处不可见的关卡将不参与 [[rebuild]] 过程；如果你的关卡很复杂，这样能大大节省时间。
- ## Reference
	- https://dev.epicgames.com/documentation/zh-cn/unreal-engine/levels-in-unreal-engine