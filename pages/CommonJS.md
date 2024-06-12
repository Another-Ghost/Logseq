- CommonJS 是一种模块化规范，最初由 Node.js 实现，用于在 JavaScript 中定义和使用模块。CommonJS 允许开发者将代码拆分为独立的模块，从而更容易维护、重用和组织代码。以下是关于 CommonJS 的详细介绍，包括其基础知识和使用示例。
- ### CommonJS 基础
- #### 导出模块
  在 CommonJS 中，通过 `module.exports` 和 `exports` 对象来导出模块的内容，使其可以在其他文件中使用。
- ##### 示例：导出函数
  ```javascript
  // math.js
  function add(a, b) {
    return a + b;
  }
  
  module.exports = add;
  ```
- ##### 示例：导出对象
  ```javascript
  // math.js
  function add(a, b) {
    return a + b;
  }
  
  function subtract(a, b) {
    return a - b;
  }
  
  module.exports = {
    add,
    subtract
  };
  ```
- #### 导入模块
  通过 `require` 函数可以导入其他模块。
- ##### 示例：导入函数
  ```javascript
  // main.js
  const add = require('./math');
  console.log(add(2, 3)); // 输出: 5
  ```
- ##### 示例：导入对象
  ```javascript
  // main.js
  const math = require('./math');
  console.log(math.add(2, 3));      // 输出: 5
  console.log(math.subtract(5, 3)); // 输出: 2
  ```
- ### 使用 CommonJS 的注意事项
  
  1. **文件路径**：
	- 使用相对路径导入本地模块，如 `./` 表示当前目录，`../` 表示上一级目录。
	- 不带路径的模块名如 `require('fs')` 表示导入核心模块或已安装的 npm 模块。
	  
	  2. **模块缓存**：
	- 模块在第一次被加载时会被缓存。之后再 `require` 同一模块时，会直接从缓存中读取，而不是重新执行模块代码。
	- 这有助于提高性能，但需要注意可能导致模块的状态共享问题。
	  
	  3. **循环依赖**：
	- 当两个或多个模块互相 `require` 时，会出现循环依赖。Node.js 会返回一个未完成的对象，这可能导致未定义的行为。避免循环依赖可以通过重构代码或使用其他设计模式解决。
- ### 示例：构建简单项目
  
  假设我们要构建一个简单的项目，包含以下结构：
  
  ```
  project/
  ├── main.js
  ├── math.js
  └── utils.js
  ```
- #### math.js
  ```javascript
  // math.js
  function add(a, b) {
    return a + b;
  }
  
  function subtract(a, b) {
    return a - b;
  }
  
  module.exports = {
    add,
    subtract
  };
  ```
- #### utils.js
  ```javascript
  // utils.js
  function greet(name) {
    return `Hello, ${name}!`;
  }
  
  module.exports = greet;
  ```
- #### main.js
  ```javascript
  // main.js
  const math = require('./math');
  const greet = require('./utils');
  
  console.log(math.add(2, 3));          // 输出: 5
  console.log(math.subtract(5, 3));     // 输出: 2
  console.log(greet('CommonJS'));       // 输出: Hello, CommonJS!
  ```
- ### 使用 npm 安装模块
  
  CommonJS 不仅可以导入本地模块，还可以导入通过 npm 安装的模块。例如，安装和使用 `lodash` 模块：
- #### 安装 lodash
  ```bash
  npm install lodash
  ```
- #### 使用 lodash
  ```javascript
  // main.js
  const _ = require('lodash');
  
  const array = [1, 2, 3, 4];
  const doubled = _.map(array, num => num * 2);
  console.log(doubled); // 输出: [2, 4, 6, 8]
  ```
- ### 结论
  
  CommonJS 是一种强大的模块化规范，广泛用于 Node.js 和其他支持 CommonJS 的环境。通过使用 `module.exports` 和 `require`，开发者可以将代码组织成独立的模块，提高代码的可维护性和重用性。了解并熟练使用 CommonJS，是 JavaScript 开发者必备的技能之一。