alias:: RepNotify function, RepNotifies

- 可指定在Actor成功接收特定变量的复制信息时要调用的^^RepNotify函数^^。[[RepNotify]]**仅在变量更新时本地触发**。响应[[authoritative Actor]]上的 变量更改 时，使用RepNotify可**减少开销**。
  id:: 653cfa4f-362c-4af4-ad3f-3bb175d5e412
  在C++中使用变量的 `UPROPERTY` 宏的 [[ReplicatedUsing]] 说明符可使用此功能，或修改蓝图中变量的 复制设置 以使用RepNotify。
- id:: 653d0ce8-0355-4f41-8cfc-5ab05f5b4c14
  #+BEGIN_TIP
  与使用[[RPC]]或[[复制函数]]相比，使用[[RepNotify]]更可取，因为它们可以添加到需要进行复制的变量上，而无论其他gameplay功能如何，这可以节省大量[[带宽]]，而无需创建额外的 *网络调用*。
  #+END_TIP
-