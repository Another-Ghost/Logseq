- |函数说明符|效果|
  |--|--|
  |[[BlueprintCallable]]|此函数可在蓝图或关卡蓝图图表中执行。|
  |[[BlueprintImplementableEvent]]|此函数可在蓝图或关卡蓝图图表中实现。|
  |[[BlueprintNativeEvent]]|此函数旨在**被蓝图重写**，但是也具有**默认原生实现**。代码中的原生函数定义的声明**名称与主函数相同但是末尾添加了`_Implementation`**的附加函数。**如果未找到任何蓝图重写，自动生成的代码将调用 `_Implementation` 方法**。|
  |[[BlueprintPure]]||
  |||