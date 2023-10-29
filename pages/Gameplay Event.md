alias:: 玩法事件

- [[Gameplay Event]]是可以被传递来 直接[[触发]][[Ability]] 的数据结构，无需通过正常通道，即可根据[[context]]发送[[data payload]]。
  id:: 653eb797-c226-4c52-80c3-704510b9880c
  常用的方法是调用[[Send Gameplay Event To Actor]]并提供实现[[IAbilitySystemInterface]]接口的 Actor 和[[Gameplay Event]]所需的[[上下文信息]]，但也可以直接在[[Ability System Event]]上调用[[Handle Gameplay Event]]。
  因为这不是调用[[Ability]]的正常方式，所以技能可能需要的[[上下文信息]]将通过[[FGameplayEventData]]数据结构传递。
  该结构是一种通用结构，不会针对任何特定的 Gameplay Event 或 Ability 进行扩展，但应该能够满足任何用例的要求。*多态[[ContextHandle]]字段* 会根据需要提供其他信息。
- id:: 653eb7f5-45f9-47b6-9348-ea8047819782
  #+BEGIN_TIP
  当 Gameplay Event 触发 Ability 时，Ability 不会通过[[Activate Ability]]代码路径运行，而是使用提供附加情境数据作为参数的"从事件激活技能"（Activate Ability From Event）。如果希望技能响应游戏事件，请务必处理此代码路径，同时还应注意，一旦在玩法技能的蓝图中实施，"从事件激活技能"（Activate Ability From Event）将取代"激活技能"（Activate Ability），让所有激活流量通过自身。
  #+END_TIP
-