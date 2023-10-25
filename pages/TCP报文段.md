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
		- ![image.png](../assets/image_1698240537963_0.png){:height 303, :width 608}
	- [[数据偏移]]
	  logseq.order-list-type:: number
	  占 4 比特，该字段的取值**以 4 字节为单位**。
	  指出TCP报文段的数据载荷部分的起始处距离 TCP 报文段的起始处有多远，这实际上指出了TCP报文段的首部长度。
	  ![image.png](../assets/image_1698241533392_0.png)
	- [[保留]]
	  logseq.order-list-type:: number
	  占 6 比特；保留为今后使用；目前应置为 0 。
		- 占 16 比特，该字段的取值以[[字节]]为单位。
		- 指出**发送本报文段的一方**的[[接收窗口]]的大小，即接收缓存的可用空间大小，这用来表征接收方的接收能力。
	- [[窗口]]
	  logseq.order-list-type:: number