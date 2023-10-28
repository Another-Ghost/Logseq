alias:: owing client, 拥有, 拥有权

- 特定 *客户端机器* 上的[[PlayerController]] *拥有* 网络游戏中的[[pawn]]。Pawn 调用[[client-only function]]时，其将无视调用函数的机器，而**仅指向拥有玩家的客户端机器**。若将Actor的[[Owner]]变量设为特定Pawn，则该Actor属于该Pawn的[[owing client]]，并将[[纯客户端函数]]指向其拥有者的机器。可使用 `IsLocallyControlled` 函数以决定Pawn是否在其[[owning client]]上。
- #+BEGIN_WARNING
  由于 *构造* 期间Pawn**可能未指定**[[Controller]]，因此避免在自定义Pawn类的 *构造函数* 中使用 `IsLocallyControlled`。
  #+END_WARNING
- 有关拥有权的详情，参见[Actor及其拥有连接](https://docs.unrealengine.com/5.3/zh-CN/actors-and-their-owning-connections-in-unreal-engine)上的指南。