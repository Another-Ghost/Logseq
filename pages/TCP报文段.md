alias:: TCP segment

- ![image.png](../assets/image_1698233876048_0.png)
- # 首部格式
  组成部分：
	- [[端口号]]：[[源端口]]和[[目的端口]]。
	  logseq.order-list-type:: number
	- TCP 实现 *可靠传输* 的相关字段
	  logseq.order-list-type:: number
		- [[序号]]
		  logseq.order-list-type:: number
		  占 32 比特，取值范围 0~2^{32}-1。当序号增加到最后一个时，下一个序号又回到 0 。
		  用来指出本TCP报文段**[[数据载荷]]的第一个字节的序号**。
		- [[确认号]]
		  logseq.order-list-type:: number
		  占 32 比特，取值范围 0~2^{32}-1。当确认号增加到最后一个时，下一个确认号又回到 0 。
		  用来指出**期望收到对方下一个TCP报文段的[[数据载荷]]的第一个字节的序号**，同时也是对之前收到的所有数据的**确认**。
		- [[确认标志位]] ACK 
		  logseq.order-list-type:: number
		  只有当 ACK 取值为 1 时，确认号字段才**有效**。ACK取值为 0 时，确认号字段**无效**。
		  TCP规定：在 TCP **连接建立后**，所有传送的TCP报文段都必须把 ACK 置 1 。
	- logseq.order-list-type:: number
-