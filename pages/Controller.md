alias:: AController, Actor/Controller

- [[Controller]]是一种可以控制[[Pawn]]（或 Pawn 的派生类，例如[[Character]]），从而控制其动作的非实体[[Actor]]。
- Controller 会接收其控制的[[Pawn]]发生的许多 *事件* 的[[通知]]。这使得 Controller 有机会对这些 *事件* 做出响应，拦截 *事件* 并取代 Pawn 的默认行为。
- 还可以设置 Controller 在给定的Pawn之前执行[[tick]]，从而最大程度地减少[[输入]]处理和[[Pawn]][[移动]]之间的 *延迟* 。
- 默认情况下，Controller 与[[Pawn]]之间是 一对一 的关系。