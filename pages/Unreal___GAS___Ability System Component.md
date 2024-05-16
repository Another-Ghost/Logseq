alias:: 技能系统组件, Ability System Component, ASC

- 与Gameplay Ability System 交互的 Actor 须拥有 ^^Ability System Component^^ 。此组件将激活[[Gameplay Ability]]、运行[[Gameplay Event]]，存储 [[Gameplay Attribute]] 、更新[[Gameplay Effect]]，和处理Actor间的交互。启用 Gameplay ability system 并创建包含技能系统组件的 Actor 后，便可创建技能并决定Actor的响应方式。
- 虽然Actor通常会有自己的技能系统组件，但是有些情况下，你会想要部分Actor（例如玩家的Pawn或角色）使用其它Actor（例如玩家状态或玩家控制器）拥有的技能系统组件。这种情况一般涉及到玩家分数或者长期存在的技能冷却计时器，因为即便是玩家的Pawn或角色被销毁并重生，或者玩家拥有一个新的Pawn或角色，这些内容也不会重置。游戏玩法技能系统便可以支持此行为；如果你需要使用它，就要编写Actor的`GetAbilitySystemComponent`函数，从而让它返回到你想要使用的技能系统组件。