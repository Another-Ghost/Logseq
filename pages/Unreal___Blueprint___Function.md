- ^^函数（Functions）^^是属于特定[[蓝图]]的 [[node graph]] ，它们可以从蓝图中的另一个 [graph]([[Blueprint Graph]]) 执行或调用。
  函数具有一个由**包含一个 [[exec output pin]]的具有函数名称的节点**指定的单一[entry point]([[Blueprint/entry point]]) 。
  当从另一个 graph 调用函数时，函数的输出执行引脚将被激活， 从而使连接的蓝图网络执行。
- ## [[pure function]]