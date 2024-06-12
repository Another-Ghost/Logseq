alias:: 跨域, Cross-Origin Resource Sharing

- 跨域（Cross-Origin Resource Sharing，CORS）是指在一个域下的网页向另一个域发起的 HTTP 请求。由于浏览器的同源策略（Same-Origin Policy），默认情况下，跨域请求会被阻止。为了允许跨域请求，需要使用 CORS。
- ### 什么是同源策略？
  同源策略是一种安全机制，限制从一个源加载的文档或脚本与另一个源的资源进行交互。一个源由协议、主机和端口组成。如果这三者有任何一个不同，则认为是不同源。
- ### 解决跨域问题的几种方法
	- **CORS（Cross-Origin Resource Sharing）**：
	  logseq.order-list-type:: number
		- 通过服务器在响应头中设置特定的 HTTP 头来允许跨域请求。
	- **JSONP（JSON with Padding）**：
	  logseq.order-list-type:: number
		- 通过 `<script>` 标签加载 JSON 数据的方式来实现跨域请求，只支持 GET 请求。
	- **代理服务器**：
	  logseq.order-list-type:: number
		- 通过一个中间服务器，服务器之间没有跨域限制，浏览器请求中间服务器，中间服务器再请求目标服务器。
	- **在 HTML 中使用 iframe**：
	  logseq.order-list-type:: number
		- 通过 `window.postMessage` 实现与 iframe 的跨域通信。
- ### 使用 CORS 解决跨域问题
  CORS 是解决跨域请求最常见的方法。它允许服务器在响应头中设置特定的头信息来告诉浏览器允许跨域请求。
	- #### 服务器设置 CORS
	- **在 Node.js 中设置 CORS**：
	  logseq.order-list-type:: number
	  使用 [cors](https://www.npmjs.com/package/cors) 中间件：
	  ```javascript
	  const express = require('express');
	  const cors = require('cors');
	  const app = express();
	  
	  app.use(cors());
	  
	  app.get('/api/data', (req, res) => {
	  res.json({ message: 'This is CORS-enabled for all origins!' });
	  });
	  
	  app.listen(3000, () => {
	  console.log('Server running on port 3000');
	  });
	  ```
	- **在 ASP.NET Core 中设置 CORS**：
	  logseq.order-list-type:: number
	  在 `Startup.cs` 文件中配置 CORS：
	  ```csharp
	  public void ConfigureServices(IServiceCollection services)
	  {
	  services.AddCors(options =>
	  {
	      options.AddPolicy("AllowAll",
	          builder =>
	          {
	              builder.AllowAnyOrigin()
	                     .AllowAnyMethod()
	                     .AllowAnyHeader();
	          });
	  });
	  
	  services.AddControllers();
	  }
	  
	  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
	  {
	  if (env.IsDevelopment())
	  {
	      app.UseDeveloperExceptionPage();
	  }
	  
	  app.UseRouting();
	  
	  app.UseCors("AllowAll");
	  
	  app.UseEndpoints(endpoints =>
	  {
	      endpoints.MapControllers();
	  });
	  }
	  ```
	- **在 Flask（Python）中设置 CORS**：
	  logseq.order-list-type:: number
	  使用 [flask-cors](https://flask-cors.readthedocs.io/en/latest/) 扩展：
	  ```python
	  from flask import Flask, jsonify
	  from flask_cors import CORS
	  
	  app = Flask(__name__)
	  CORS(app)
	  
	  @app.route('/api/data')
	  def get_data():
	  return jsonify(message='This is CORS-enabled for all origins!')
	  
	  if __name__ == '__main__':
	  app.run(port=5000)
	  ```
	- #### 客户端发起跨域请求
	  使用 JavaScript 的 `fetch` API 发起跨域请求：
	  ```javascript
	  fetch('http://localhost:3000/api/data')
	  .then(response => response.json())
	  .then(data => console.log(data))
	  .catch(error => console.error('Error:', error));
	  ```
- ### 使用 JSONP 解决跨域问题
  JSONP 是一种通过 `<script>` 标签来进行跨域请求的技术，只支持 GET 请求。它利用 `<script>` 标签可以跨域加载资源的特点来获取数据。
  ```html
  <!DOCTYPE html>
  <html>
  <head>
    <title>JSONP Example</title>
  </head>
  <body>
    <script>
        function handleResponse(data) {
            console.log(data);
        }
    </script>
    <script src="http://example.com/api/data?callback=handleResponse"></script>
  </body>
  </html>
  ```
- ### 使用代理服务器解决跨域问题
  通过代理服务器，可以避免浏览器的同源策略限制。你可以使用任何支持 HTTP 请求转发的服务器（例如 Nginx、Apache 或 Node.js 中间件）。
	- #### 使用 Node.js 代理服务器
	  ```javascript
	  const express = require('express');
	  const request = require('request');
	  const app = express();
	  
	  app.use('/api', (req, res) => {
	  const url = 'http://example.com' + req.url;
	  req.pipe(request(url)).pipe(res);
	  });
	  
	  app.listen(3000, () => {
	  console.log('Proxy server running on port 3000');
	  });
	  ```
- ### 结论
	- **CORS** 是解决跨域请求最常见和推荐的方法，它通过服务器设置 HTTP 头信息来允许跨域请求。
	- **JSONP** 适用于需要支持老式浏览器并且只需要发起 GET 请求的场景。
	- **代理服务器** 是一种通过中间服务器转发请求的方法，适用于需要更多控制和定制化的场景。
	- **iframe** 和 `window.postMessage` 可用于特定场景的跨域通信。
	  根据具体需求选择合适的方法来解决跨域问题。
	  <!--Converted by ToLogseq-->