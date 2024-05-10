- 要使用npm生成默认的package.json文件，你可以在终端中运行 `npm init -y` 命令。这将创建一个预填充的package.json文件。
- ```bash
  npm init -y
  ```
- 这将生成一个如下所示的默认package.json文件：
- ```json
  {
  "name": "your-package-name",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
  }
  ```
- `-y`标志意味着对所有问题的默认答案是“yes”。
-