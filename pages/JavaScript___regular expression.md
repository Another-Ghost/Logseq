- 在JavaScript中，正则表达式是用于匹配字符串中字符组合的模式。它们可以用于验证、搜索、替换文本等操作。JavaScript中的正则表达式通常被包含在斜杠`/`符号之间，后面可以跟随一些标志以改变正则表达式的行为。
- ### 创建正则表达式
  
  有两种方式在JavaScript中创建正则表达式：
	- **使用字面量语法**：直接在两个斜杠之间写入表达式。\boldsymbol
	  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  ```javascript
		   let regex = /ab+c/;
		   ```
	- **使用`RegExp`构造函数**：传递一个字符串作为参数。
	  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  ```javascript
		  let regex = new RegExp('ab+c');
		  ```
- ### 常用标志
- `g`：全局搜索（不会在找到第一个匹配后停止）。
- `i`：不区分大小写。
- `m`：多行搜索。
- `u`：Unicode模式，用于支持Unicode码点的完整字符。
- `y`：粘性搜索，匹配从目标字符串的当前位置开始。
- ### 常用方法
- **test()**：测试字符串是否匹配模式，返回`true`或`false`。
  
  ```javascript
  let regex = /hello/;
  console.log(regex.test('hello world'));  // 输出 true
  ```
- **exec()**：在字符串中执行搜索匹配，返回一个结果数组或`null`。
  
  ```javascript
  let result = regex.exec('hello world');
  console.log(result[0]);  // 输出 'hello'
  ```
- **match()**：字符串方法，执行正则表达式匹配。
  
  ```javascript
  let matchResult = 'hello world'.match(/hello/);
  console.log(matchResult[0]);  // 输出 'hello'
  ```
- **replace()**：字符串方法，执行查找和替换。
  
  ```javascript
  let replacedString = 'hello world'.replace(/hello/, 'goodbye');
  console.log(replacedString);  // 输出 'goodbye world'
  ```
- **search()**：字符串方法，搜索匹配的字符串，返回第一个匹配项的索引。
  
  ```javascript
  let index = 'hello world'.search(/world/);
  console.log(index);  // 输出 6
  ```
- **split()**：字符串方法，使用正则表达式来分割字符串。
  
  ```javascript
  let parts = 'hello world'.split(/\s/);
  console.log(parts);  // 输出 ['hello', 'world']
  ```
- ### 使用分组
  
  在正则表达式中，括号`()`用于分组，可以从匹配的字符串中提取部分内容。
  
  ```javascript
  let regexGroup = /(\w+) (\w+)/;
  let resultGroup = regexGroup.exec('hello world');
  console.log(resultGroup[1]);  // 输出 'hello'
  console.log(resultGroup[2]);  // 输出 'world'
  ```
  
  在这个例子中，`\w+`匹配一个或多个字母或数字，括号创建了分组，`exec`方法返回的数组中包含了整个匹配结果及各个分组的匹配结果。
  
  正则表达式是处理字符串的强大工具，但它们也可以变得非常复杂。理解基本的构造和方法是有效使用正则表达式的关键。在实际应用中，应当根据具体需求来构建合适的正则表达式，并通过测试确保它们的正确性。
- ### 替换特殊字符
  在 `replace()` 中使用 `$` 字符时需要特别注意，因为它用来指代捕获组。有几个特殊的序列：
	- `$$`：插入一个 "$"。
	- `$&`：插入整个匹配。
	- `$\``：插入当前匹配前的内容。
	- `$'`：插入当前匹配后的内容。
	- `$n`（其中 n 是从 1 到 99 的数字）：引用第 n 个捕获组的匹配内容。
	  这些特殊字符使得 `replace()` 在进行文本处理时非常灵活和强大。
-