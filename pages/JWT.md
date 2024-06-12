alias:: JSON web Token

- JSON Web Token（JWT）是一种紧凑的、URL安全的令牌格式，用于在各方之间传递信息。它常用于身份验证和信息交换。JWT 是由三部分组成的字符串，每部分之间使用点（`.`）分隔：
	- **Header（头部）**：包含令牌的元数据，如类型和签名算法。
	  logseq.order-list-type:: number
	- **Payload（有效载荷）**：包含声明（claims），即传递的信息数据。
	  logseq.order-list-type:: number
	- **Signature（签名）**：用于验证令牌的真实性，确保令牌未被篡改。
	  logseq.order-list-type:: number
- ### JWT 的结构 
  logseq.order-list-type:: number
	- JWT 的结构如下：
	  ```
	  header.payload.signature
	  ```
	- #### Header
		- 头部通常包括两部分信息：
			- `typ`：声明类型，通常是 `JWT`。
			- `alg`：声明加密算法，通常是 `HS256`（HMAC SHA256）或 `RS256`（RSA SHA256）。
		- 例如：
		  ```json
		  {
		  "typ": "JWT",
		  "alg": "HS256"
		  }
		  ```
	- #### Payload
	- 有效载荷包含声明，可以是关于实体（通常是用户）和其他数据的声明。常见的声明包括：
		- `iss`（Issuer）：签发者
		- `sub`（Subject）：主题
		- `aud`（Audience）：受众
		- `exp`（Expiration time）：过期时间
		- `nbf`（Not before）：生效时间
		- `iat`（Issued at）：签发时间
		- `jti`（JWT ID）：唯一标识符
		- 例如：
		  ```json
		  {
		  "sub": "1234567890",
		  "name": "John Doe",
		  "admin": true
		  }
		  ```
		- #### Signature
		- 签名部分是用于验证消息没有被篡改。签名是通过对头部和有效载荷进行编码，再使用密钥加密生成的。签名算法如下：
		  ```
		  HMACSHA256(
		  base64UrlEncode(header) + "." + base64UrlEncode(payload),
		  secret
		  )
		  ```
- ### 如何生成和验证 JWT 
  logseq.order-list-type:: number
- #### 生成 JWT
- 可以使用多种编程语言和库生成 JWT。以下是使用 Node.js 和 `jsonwebtoken` 库生成 JWT 的示例：
  ```javascript
  const jwt = require('jsonwebtoken');
  
  const payload = {
  sub: "1234567890",
  name: "John Doe",
  admin: true
  };
  
  const secret = 'your-256-bit-secret';
  
  const token = jwt.sign(payload, secret, { algorithm: 'HS256' });
  
  console.log(token);
  ```
- #### 验证 JWT
- 验证 JWT 以确保令牌的真实性和完整性。以下是使用 Node.js 和 `jsonwebtoken` 库验证 JWT 的示例：
  ```javascript
  const jwt = require('jsonwebtoken');
  
  const token = 'your.jwt.token';
  const secret = 'your-256-bit-secret';
  
  try {
  const decoded = jwt.verify(token, secret);
  console.log(decoded);
  } catch (err) {
  console.error('Token is invalid or expired');
  }
  ```
- ### 使用 JWT 进行身份验证 
  logseq.order-list-type:: number
- JWT 常用于身份验证。在这种情况下，当用户登录时，服务器会生成一个 JWT 并返回给客户端。客户端会将该 JWT 存储在本地存储或 cookie 中，并在每次请求时将其包含在 `Authorization` 头部发送给服务器。服务器验证 JWT 并授权用户访问资源。
- ### 示例流程
	- **用户登录**：
	  logseq.order-list-type:: number
		- 用户向服务器发送用户名和密码。
		- 服务器验证用户信息，生成 JWT 并返回。
	- **客户端存储 JWT**：
	  logseq.order-list-type:: number
		- 客户端将 JWT 存储在本地存储或 cookie 中。
	- **请求受保护资源**：
	  logseq.order-list-type:: number
		- 客户端在请求受保护资源时，将 JWT 包含在 `Authorization` 头部发送给服务器。
		- 服务器验证 JWT 并返回请求的资源。
- #### 前端示例（使用 Fetch API）：
  ```javascript
  // 用户登录后存储 JWT
  fetch('https://example.com/login', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ username: 'user', password: 'pass' })
  })
  .then(response => response.json())
  .then(data => {
    localStorage.setItem('token', data.token);
  });
  
  // 请求受保护资源
  const token = localStorage.getItem('token');
  
  fetch('https://example.com/protected', {
  method: 'GET',
  headers: {
    'Authorization': `Bearer ${token}`
  }
  })
  .then(response => response.json())
  .then(data => {
    console.log(data);
  });
  ```
- ### 总结
- JWT 是一种方便、安全的在各方之间传递信息的方式，广泛用于身份验证和信息交换。通过理解其结构和工作原理，可以有效地使用 JWT 进行安全通信和身份验证。
  <!--Converted by ToLogseq-->