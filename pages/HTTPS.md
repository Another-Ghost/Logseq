alias:: HyperText Transfer Protocol Secure, 超文本传输协议安全版

- HTTPS（超文本传输协议安全版，HyperText Transfer Protocol Secure）是 HTTP 的安全版本，它在传输数据时通过加密来保证通信的安全性和完整性。HTTPS 防止数据在互联网上传输时被窃听、篡改或者伪造。
- ### HTTPS 的工作原理
- HTTPS 在传输数据之前，使用 ^^SSL（Secure Sockets Layer）^^或 ^^TLS（Transport Layer Security）^^协议进行[[加密]]处理。这些协议提供端到端的数据加密，确保在客户端与服务器之间传输的任何信息都无法被第三方轻易读取或修改。
- #### 加密过程涉及以下几个关键步骤：
	- **握手阶段**：
	  logseq.order-list-type:: number
		- 客户端和服务器开始通信时首先进行握手。
		- 客户端发送支持的加密方法（密码套件），包括加密算法与密钥交换方法。
		- 服务器选择一组加密算法与密钥交换方法，并发送自己的身份信息，通常包括一个由^^权威证书颁发机构（CA）^^签名的SSL/TLS证书。
		- 客户端验证服务器证书的有效性，确保证书由可信的 CA 签名且未过期。
		- 客户端和服务器协商生成“会话密钥”，用于本次会话的加密。
	- **数据传输阶段**：
	  logseq.order-list-type:: number
		- 使用会话密钥，客户端和服务器开始加密通信，保证数据的安全与完整性。
	- **会话结束**：
	  logseq.order-list-type:: number
		- 通信结束后，会话密钥被废弃，保证即使密钥被获取也无法解密其他会话的数据。
- ### HTTPS 的优点
	- **数据加密**：确保用户数据如密码、银行信息等敏感信息在互联网上传输时不被窃听。
	  logseq.order-list-type:: number
	- **数据完整性**：数据在传输过程中不能被修改或损坏，未经授权的更改可以被检测出来。
	  logseq.order-list-type:: number
	- **身份验证**：帮助用户确认他们正在与预期的服务器通信，而非被重定向到一个恶意的站点。
	  logseq.order-list-type:: number
- ### HTTPS 的使用
	- 当你访问一个网站时，如果 URL 以 `https://` 开头，这意味着该网站使用 HTTPS，并在传输数据时加密信息。
	- 现代浏览器如 Chrome、Firefox 等会在网址栏显示锁形图标，表示当前的会话是加密的。
- ### 为什么需要 HTTPS
	- 随着网络安全威胁的增加，使用 HTTPS 已经成为网站的一项基本安全措施。Google 等搜索引擎优化（SEO）也更倾向于对使用 HTTPS 的网站给予更好的排名。此外，一些新的网络功能，如 HTTP/2，通常只在加密连接上可用。
-