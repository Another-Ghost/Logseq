- JSON (JavaScript Object Notation) 是一种轻量级的数据交换格式，易于人类阅读和编写，同时也易于机器解析和生成。JSON 与 JavaScript 有着紧密的关系，因为它基于 JavaScript 对象表示法，但它独立于编程语言，被广泛用于不同语言的数据交换。以下是关于 JSON 和 JavaScript 的一些关键点和示例：
- ### JSON 和 JavaScript 的关系
	- **JSON 的格式**：
	  logseq.order-list-type:: number
	  JSON 使用键值对来表示数据，类似于 JavaScript 对象。以下是一个 JSON 的示例：```json
	  {
	     "name": "John",
	     "age": 30,
	     "isStudent": false,
	     "courses": ["Math", "Science"],
	     "address": {
	         "street": "123 Main St",
	         "city": "New York"
	     }
	  }
	  ```
	  - **JavaScript 对象**：
	  logseq.order-list-type:: number
	  JavaScript 对象的语法与 JSON 非常相似，但存在一些差异。以下是一个 JavaScript 对象的示例：```javascript
	  const person = {
	     name: "John",
	     age: 30,
	     isStudent: false,
	     courses: ["Math", "Science"],
	     address: {
	         street: "123 Main St",
	         city: "New York"
	     }
	  };
	  ```
- ### JSON 与 JavaScript 的转换
	- **将 JavaScript 对象转换为 JSON 字符串**：
	  logseq.order-list-type:: number
	  使用 `JSON.stringify()` 方法可以将 JavaScript 对象转换为 JSON 字符串。
	  ```javascript
	  const jsonString = JSON.stringify(person);
	  console.log(jsonString);
	  // 输出: {"name":"John","age":30,"isStudent":false,"courses":["Math","Science"],"address":{"street":"123 Main St","city":"New York"}}
	  ```
	  **将 JSON 字符串转换为 JavaScript 对象**：
	  使用 `JSON.parse()` 方法可以将 JSON 字符串转换为 JavaScript 对象。
	  ```javascript
	  const jsonString = '{"name":"John","age":30,"isStudent":false,"courses":["Math","Science"],"address":{"street":"123 Main St","city":"New York"}}';
	  const personObject = JSON.parse(jsonString);
	  console.log(personObject);
	  // 输出: { name: 'John', age: 30, isStudent: false, courses: [ 'Math', 'Science' ], address: { street: '123 Main St', city: 'New York' } }
	  ```
- ### 注意事项
	- **JSON 键名必须用双引号**：
	  logseq.order-list-type:: number
	  在 JSON 格式中，键名必须用双引号包围，而在 JavaScript 对象中则不要求。
	  ```json
	  { "name": "John" } // 合法的 JSON
	  { name: "John" }   // 非法的 JSON
	  ```
	- **JSON 不支持函数和 undefined**：
	  logseq.order-list-type:: number
	  JSON 仅支持字符串、数字、布尔值、数组、对象和 null，不支持函数和 undefined。
	  ```javascript
	  const obj = {
	     name: "John",
	     greet: function() { console.log("Hello!"); },
	     age: undefined
	  };
	  const jsonString = JSON.stringify(obj);
	  console.log(jsonString);
	  // 输出: {"name":"John"}
	  ```
- ### JSON 的使用场景
	- **数据存储**：
	  logseq.order-list-type:: number
	  JSON 通常用于配置文件和数据存储，如在 NoSQL 数据库（如 MongoDB）中使用 JSON 格式存储数据。
	- **数据传输**：
	  logseq.order-list-type:: number
	  JSON 常用于客户端和服务器之间的数据交换，例如通过 AJAX 请求传递 JSON 数据。
	  ```javascript
	  fetch('https://api.example.com/data')
	     .then(response => response.json())
	     .then(data => console.log(data))
	     .catch(error => console.error('Error:', error));
	  ```
- 通过掌握 JSON 和 JavaScript 之间的关系及其转换方法，你可以更高效地在前端和后端之间进行数据交换和处理。JSON 的简洁性和易用性使其成为现代 Web 开发中不可或缺的一部分。