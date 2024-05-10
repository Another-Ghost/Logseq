alias:: 关卡流送体积, 关卡流送体积域

- 流送关卡的 ^^加载/卸载请求^^的发出 是基于视点是否处于该关卡关联的^^关卡流送体积域^^中。
  collapsed:: true
	- > 基于体积域的关卡流送易于使用，不要求脚本编写，是控制关卡流送的理想方式。 此外，基于体积域的关卡流送和基于脚本的流送相比更易于维护：加载系统的需求发生变化时，调整体积域的大小即可对关卡加载/卸载行为进行修改。
- 具体而言，关卡流送体积域可以两种方式使用：
	- **游戏** 中，玩家视点处于体积域中时，关卡流送体积域将使关卡加载；玩家视点处于体积域外时，关卡将卸载。
	- **编辑器** 中，关卡流送体积域可基于透视视口摄像机的位置**自动隐藏/取消隐藏**关卡，用于预览关卡流送。
- ## Reference
	- TODO https://dev.epicgames.com/documentation/zh-cn/unreal-engine/level-streaming-volumes-reference-in-unreal-engine
	- Procedural World
	  TODO https://dev.epicgames.com/documentation/zh-cn/unreal-engine/loading-and-unloading-levels-using-blueprints-in-unreal-engine