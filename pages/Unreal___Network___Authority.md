alias:: authority, 主控权

- 拥有某一 [[actor]] 的 ^^authority^^ 的[[引擎实例]]则掌管 Actor 的复制 。
- 要确定当前运行的引擎实例是否有主控权，需要查看 [[Role]] 属性是否为 `ROLE_Authority`。
- 就目前而言，**只有[[服务器]]能够向已连接的[[客户端]]同步 Actor （客户端永远都不能向服务器同步）**。
  始终记住这一点， **只有**服务器才能看到 `Role == ROLE_Authority` 和 `RemoteRole == ROLE_SimulatedProxy` 或者 `ROLE_AutonomousProxy`。这也说明了服务器的引擎实例负责将此 actor 复制到远程连接。