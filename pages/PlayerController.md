alias:: Controller/PlayerController

- ^^PlayerController^^是玩家控制 Pawn 的接口。
- PlayerController 是 被控[[Pawn]] 的 [[owner]]  。
- ## 总结
	- 什么情况下在 PlayerController 中处理输入：
	  logseq.order-list-type:: number
		- 一个游戏客户端上有**多个 player** ；
		  logseq.order-list-type:: number
		- 需要在运行时**动态更换 Pawn**。
		  logseq.order-list-type:: number
			- 某些情况下，则必须把[[输入]]处理或其他功能放到[[PlayerController]]中。PlayerController在整个游戏在过程中都是**一直存在**的，但是[[Pawn]]可能是**临时存在**的。
-