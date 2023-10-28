alias:: RepNotify function

- 可指定在Actor成功接收特定变量的复制信息时要调用的[[RepNotify函数]]。[[RepNotify]]**仅在变量更新时本地触发**。触发 *gameplay逻辑* 响应[[authoritative Actor]]上的变量更改时，使用RepNotify可减少开销。在C++中使用变量的 `UPROPERTY` 宏的 `ReplicatedUsing` 说明符可访问此功能，或修改蓝图中变量的复制设置以使用RepNotify。
  id:: 653cfa4f-362c-4af4-ad3f-3bb175d5e412
-