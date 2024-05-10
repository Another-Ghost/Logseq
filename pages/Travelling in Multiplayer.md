alias:: 多人游戏中的关卡切换

- 虚幻引擎（UE）中主要有两种转移方式：^^无缝^^和^^非无缝^^方式。两者的主要区别在于，
	- [[seamless travel]] 是一种非阻塞（[[non-blocking]]）操作，
	- 而 [[non-seamless travel]] 则是一种阻塞（[[blocking]]）操作。
- 当客户端执行[[非无缝转移]]时，[[客户端]]将与[[服务器]]**断开连接**，然后重新连接到同一服务器，而服务器将准备新的地图以供加载。
  建议虚幻引引擎多人模式游戏尽量采用[[无缝转移]]。这样做通常可以提供更流畅的体验，同时避免重新连接过程中可能出现的问题。
- 有三种情形中**必然产生[[非无缝转移]]**：
	- 初次加载地图时；
	  logseq.order-list-type:: number
	- 初次作为客户端连接服务器时；
	  logseq.order-list-type:: number
	- 想要终止一个多人模式游戏并启动新游戏时。
	  logseq.order-list-type:: number
- 有三个用来驱动[[转移]]的主要函数：UEngine::Browse、UWorld::ServerTravel 和APlayerController::ClientTravel。遵循下面的准则来确定使用哪个函数:
	- ### [[UEngine::Browse]] ：
		- 像是加载新地图时的硬重置。
		  logseq.order-list-type:: number
		- 始终导致[[非无缝切换]]。
		  logseq.order-list-type:: number
		- 导致服务器在切换到目标地图前与当前客户端断开连接。
		  logseq.order-list-type:: number
		- 专用服务器无法切换至其他服务器，因此 **[[map]] 必须存储在本地**（不能是URL）。
		  logseq.order-list-type:: number
	- ### [[UWorld::ServerTravel]] ：
		- 仅适用于服务器。
		- 会将服务器跳转到新的世界/场景。
		- 所有连接的客户端都会跟随。
		- 这就是多人游戏在地图之间转移时所用的方法，而服务器将负责调用此函数。
		- 服务器将为所有已连接的[[客户端玩家]]调用 [[APlayerController::ClientTravel]] 。
	- ### [[APlayerController::ClientTravel]]
		- 如果从客户端调用，则转移到新的服务器。
		- 如果从服务器调用，则要求特定客户端转移到新地图（但仍然连接到当前服务器）。
- ## Reference
	- TODO https://dev.epicgames.com/documentation/en-us/unreal-engine/travelling-in-multiplayer-in-unreal-engine
-