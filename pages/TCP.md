alias:: 传输控制协议, Transmission Control Protocol

- TCP是[[面向连接]]的协议，它基于[[运输连接]]来传送[[TCP报文段]]。
- *TCP 运输连接* 的建立和释放，是每一次 *面向连接* 的通信中必不可少的过程。
  TCP运输连接有以下三个阶段：
	- 通过[[三报文握手]]来 *建立TCP连接* 。
	  logseq.order-list-type:: number
	- 基于已建立的TCP连接进行 *可靠* 的数据传输。
	  logseq.order-list-type:: number
	- 在数据传输结束后，还要通过[[四报文挥手]]来 *释放TCP连接* 。
	  logseq.order-list-type:: number