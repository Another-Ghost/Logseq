alias:: 玩法事件

- [[Gameplay Event]]是可以被传递来 直接[[触发]][[Ability]] 的数据结构，无需通过正常通道，即可根据[[context]]发送[[data payload]]。
  常用的方法是调用[[Send Gameplay Event To Actor]]并提供实现[[IAbilitySystemInterface]]接口的 Actor 和[[Gameplay Event]]所需的 *上下文信息* ，但也可以直接在上调用Handle Gameplay Event。因为这不是调用玩法技能的正常方式，所以技能可能需要的情境信息将通过`FGameplayEventData`数据结构传递。该结构是一种通用结构，不会针对任何特定的玩法事件或技能进行扩展，但应该能够满足任何用例的要求。多态`ContextHandle`字段会根据需要提供其他信息。
-
-