- 一个默认的空白HTML文档是创建新Web项目的基本起点。它包含HTML的基本结构，准备好可扩展的框架，以便将来添加内容、样式和脚本。以下是一个典型的默认空白HTML文档的示例：
  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8"> <!-- 设置字符编码 -->
      <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- 响应式设计 -->
      <title>Blank Page</title> <!-- 页面标题 -->
  </head>
  <body>
      <!-- 页面内容 -->
  </body>
  </html>
  ```
- ### 这个默认空白HTML文档包含的主要元素
	- **DOCTYPE声明**：
	  logseq.order-list-type:: number
	  ```html
	  <!DOCTYPE html>
	  ```
	  指定文档使用的HTML版本。在现代Web开发中，这通常是HTML5。
	- **`<html>` 根标签**：
	  logseq.order-list-type:: number
	  ```html
	  <html lang="en">
	  ```
	  包围整个HTML文档。`lang="en"` 指定了页面的语言。
	- **`<head>` 部分**：
	  logseq.order-list-type:: number
		- **字符编码**：
		  ```html
		  <meta charset="UTF-8">
		  ```
		  指定文档使用UTF-8字符编码，确保支持多种语言和字符。
		- **视图窗口设置**：
		  ```html
		  <meta name="viewport" content="width=device-width, initial-scale=1.0">
		  ```
		  设置视图窗口，确保页面在移动设备上具有响应式设计。
		- **页面标题**：
		  ```html
		  <title>Blank Page</title>
		  ```
		  浏览器标签页上显示的标题。
	- **`<body>` 部分**：
	  logseq.order-list-type:: number
	  ```html
	  <body>
	     <!-- 页面内容 -->
	  </body>
	  ```
	  这是页面内容的主体部分。未来可以在这里添加文本、图像、表单、表格等。
- ### 拓展和定制
  这个默认空白文档为你提供了基本结构，之后可以根据需求进行拓展：
	- **样式表**：在 `<head>` 部分添加链接到外部CSS样式表，或直接嵌入样式定义。
	  ```html
	  <link rel="stylesheet" href="styles.css">
	  ```
	- **JavaScript**：在 `<head>` 部分或 `<body>` 的末尾添加外部或内联的JavaScript脚本。
	  ```html
	  <script src="script.js"></script>
	  ```
	- **页面内容**：在 `<body>` 部分添加HTML内容，如段落、标题、图像、链接、表格、表单等。
- 通过这个默认的空白HTML文档，你可以开始构建和开发各种类型的Web内容，并根据项目需求逐步完善和扩展。