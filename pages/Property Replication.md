alias:: 属性复制, 变量复制, Variable Replication

- 在 C++ 中对 *变量* 和 *对象引用* 进行[[复制]]需要使用对应[[UPROPERTY]]宏内的 `Replicated` 或 `ReplicateUsing` 说明符，或在蓝图的细节面板中将它们指定为`Replicated`。 [[authoritative Actor]]上[[replicated variable]]的值变更时，其信息将自动从authoritative Actor发送到连接会话的[[远程代理]]。
- ## [[RepNotity]]