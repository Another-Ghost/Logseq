alias:: AController, Actor/Controller

- ## 概念
  [[Controller]]是一种可以[[possess]]一个[[Pawn]]，从而控制其行动的非实体 Actor。
- ## 说明
	- Controller 会接收其持有的 Pawn 发出的事件通知。这使得 Controller 有机会对这些事件做出响应，**拦截事件并取代** Pawn 的默认行为。
		- 如可以设置 Controller 在给定的Pawn之前执行[[tick]]，从而最大程度地减少[[输入处理]]和 Pawn [[移动]]之间的延迟。
	- 默认情况下，Controller 与 Pawn 之间是**一对一**的关系。
	-
-