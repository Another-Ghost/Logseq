alias:: 玩法标记

- 每种 [[Gameplay Ability]] 都拥有一组[[Gameplay Tag]]，以可影响其行为的方式 识别 和 分类 技能。
  还有[[Gameplay Tag Container]]和[[Gameplay Tag Query]]，用于支持与其他技能进行交互。
- |Gameplay Tag Variable|目的|
  |--|--|
  |Cancel Abilities With Tag|如果任何已在执行的技能带有与 执行此技能时 提供的 *列表* 匹配的 Tag ，则[取消]([[取消技能]])那些技能。|
  |Block Abilities With Tag|在 执行此技能时，[[阻止]]执行具有匹配 Tag 的任何其他技能。|
  |Activation Owned Tags|在 执行此技能时，技能的所有者将被[[授予]]这组 Tag。|
  |Activation Required Tags|只有 *activating Actor 或 Component* **具有所有**这些 Tag 时，技能才会被[[激活]]。|
  |Activation Blocked Tags|只有 *activating Actor 或 Component* **没有任何** 这些 Tag 时，技能才会被[[激活]]。|
  |Target Required Tags|只有 *targeted Actor 或 Component* **具有所有**这些 Tag 时，技能才会被[[激活]]。|
  |Target Blocked Tags|只有 *targeted  Actor或 Component* **没有任何**这些 Tag 时，技能才会被[[激活]]。|