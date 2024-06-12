- Insomnia 是一个流行的 API 调试工具，用于测试和调试 RESTful 和 GraphQL API。它提供了一个直观的用户界面，让开发者可以轻松地发送请求、查看响应，并管理 API 请求。以下是关于 Insomnia Requests 的一些详细介绍和使用示例。
- ### 安装 Insomnia
  你可以从 [Insomnia 官网](https://insomnia.rest/) 下载并安装适用于 macOS、Windows 或 Linux 的版本。
- ### 创建请求
	- **启动 Insomnia**：
	  logseq.order-list-type:: number
	  打开 Insomnia 应用程序。
	- **创建新请求**：
	  logseq.order-list-type:: number
		- 点击左上角的 “+” 按钮，选择 “New Request”。
		- 为请求命名并选择请求类型（如 GET、POST、PUT、DELETE 等）。
	- **配置请求**：
	  logseq.order-list-type:: number
		- 输入请求的 URL。
		- 选择请求方法（GET、POST、PUT、DELETE 等）。
		- 配置请求头（Headers）、请求体（Body）和查询参数（Query Parameters）等。
- ### 发送请求和查看响应
	- **发送请求**：
	  logseq.order-list-type:: number
		- 配置完请求后，点击右上角的 “Send” 按钮发送请求。
	- **查看响应**：
	  logseq.order-list-type:: number
		- 请求发送后，可以在下方查看服务器返回的响应数据，包括响应状态码、响应头和响应体。
- ### 使用环境变量
  Insomnia 允许你使用环境变量来管理和复用请求中的一些参数（如 Base URL、API Key 等）。这对于处理不同的环境（开发、测试、生产）非常有用。
	- **创建环境**：
	  logseq.order-list-type:: number
		- 在左侧面板中，点击环境变量按钮（齿轮图标），选择 “Manage Environments”。
		- 创建新环境，命名为 “Development”，并添加环境变量。例如：
		  ```json
		  {
		  "base_url": "https://api.example.com",
		  "api_key": "your_api_key"
		  }
		  ```
	- **在请求中使用环境变量**：
	  logseq.order-list-type:: number
		- 在请求的 URL 和头信息中，可以使用 `{{base_url}}` 和 `{{api_key}}` 来引用环境变量。例如：
		  ```url
		  {{base_url}}/endpoint
		  ```
		  添加请求头：
		  ```plaintext
		  Authorization: Bearer {{api_key}}
		  ```
- ### 示例：发送 GET 请求
	- **创建 GET 请求**：
	  logseq.order-list-type:: number
		- 点击 “+” 按钮，选择 “New Request”，命名为 “Get User”。
		- 设置方法为 `GET`，输入 URL，例如：
		  ```url
		  {{base_url}}/users/1
		  ```
	- **发送请求**：
	  logseq.order-list-type:: number
		- 点击 “Send” 按钮，查看响应。
- ### 示例：发送 POST 请求
	- **创建 POST 请求**：
	  logseq.order-list-type:: number
		- 点击 “+” 按钮，选择 “New Request”，命名为 “Create User”。
		- 设置方法为 `POST`，输入 URL，例如：
		  ```url
		  {{base_url}}/users
		  ```
	- **设置请求体**：
	  logseq.order-list-type:: number
		- 选择 “Body” 选项卡，选择类型为 `JSON`，输入请求体数据，例如：
		  ```json
		  {
		  "name": "John Doe",
		  "email": "john.doe@example.com"
		  }
		  ```
	- **发送请求**：
	  logseq.order-list-type:: number
		- 点击 “Send” 按钮，查看响应。
- ### 使用 Insomnia 插件
  Insomnia 支持使用插件来扩展其功能。你可以从 Insomnia 插件库中安装各种插件，或自行开发插件。
	- **安装插件**：
	  logseq.order-list-type:: number
		- 点击左下角的齿轮图标，选择 “Plugins”。
		- 搜索并安装你需要的插件。
	- **使用插件**：
	  logseq.order-list-type:: number
		- 安装后，插件会自动集成到 Insomnia 的界面中，你可以在相关功能区域中使用它们。
- ### 总结
  Insomnia 是一个强大而灵活的 API 调试工具，适合开发者用来测试和调试 API 请求。通过其直观的界面和丰富的功能，开发者可以轻松地创建、发送和管理 API 请求，并使用环境变量和插件来提升工作效率。无论是处理简单的 RESTful API 还是复杂的 GraphQL 查询，Insomnia 都能提供强大的支持。
  <!--Converted by ToLogseq-->