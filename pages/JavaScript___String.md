- 在JavaScript中，`String`是一种基本的数据类型，用于表示文本数据。字符串可以包含字母、数字、符号和空格，或者任何其他的文本字符。
- ### 创建字符串
  
  字符串可以通过两种方式创建：
  
  1. **字面量方式**：直接使用引号（单引号`'`、双引号`"`或反引号`` ` ``）包围文本。
  
   ```javascript
   let str1 = 'Hello, World!';
   let str2 = "Hello, World!";
   let str3 = `Hello, World!`;  // 反引号用于模板字符串
   ```
  
  2. **String对象构造函数**：使用`new`关键字和`String`构造函数。
  
   ```javascript
   let str4 = new String("Hello, World!");
   ```
  
  通常推荐使用字面量方式创建字符串，因为它不涉及对象构造函数的调用，更简洁且性能更好。
- ### 字符串属性和方法
  
  JavaScript中的字符串对象拥有多种方法和属性，可以用来操作和查询字符串。以下是一些常用的属性和方法：
- **length**：属性，返回字符串的长度。
  
  ```javascript
  console.log('Hello, World!'.length);  // 输出 13
  ```
- **charAt(index)**：方法，返回指定位置的字符。
  
  ```javascript
  console.log('Hello'.charAt(1));  // 输出 'e'
  ```
- **concat(string2, string3, ..., stringN)**：方法，将一个或多个字符串与原字符串连接并返回新字符串。
  
  ```javascript
  console.log('Hello'.concat(' ', 'World', '!'));  // 输出 'Hello World!'
  ```
- **indexOf(substring)**：方法，返回子字符串在字符串中首次出现的位置，如果未找到子字符串，则返回-1。
  
  ```javascript
  console.log('Hello, World!'.indexOf('World'));  // 输出 7
  ```
- **slice(startIndex, endIndex)**：方法，提取字符串的一部分并返回新字符串，不改变原字符串。
  （提取到 `endIndex` 之前）
- ```javascript
  console.log('Hello, World!'.slice(7, 12));  // 输出 'World'
  ```
- **split(separator, limit)**：方法，使用指定的分隔符字符串将原字符串分割成多个子字符串，并返回它们组成的数组。
  
  ```javascript
  console.log('Hello, World!'.split(', '));  // 输出 ['Hello', 'World!']
  ```
- **replace(searchValue, newValue)**：方法，返回一个新字符串，其中的某些子字符串被替换为新的字符串。
  
  ```javascript
  console.log('Hello, World!'.replace('World', 'Everyone'));  // 输出 'Hello, Everyone!'
  ```
- **toUpperCase()** 和 **toLowerCase()**：方法，分别将字符串转换为大写或小写。
  
  ```javascript
  console.log('Hello, World!'.toUpperCase());  // 输出 'HELLO, WORLD!'
  console.log('Hello, World!'.toLowerCase());  // 输出 'hello, world!'
  ```
- **trim()**：方法，从字符串的两端删除空白字符。
  
  ```javascript
  console.log('   Hello, World!   '.trim());  // 输出 'Hello, World!'
  ```
- ### 模板字符串
  
  使用反引号（`` ` ``）创建的模板字符串可以包含占位符，占位符由`${expression}`表示，其中的`expression`是一个JavaScript表达式。模板字符串可以跨行，并且可以包含表达式、变量和其他JavaScript代码。
  
  ```javascript
  let name = 'World';
  let greeting = `Hello, ${name}!`;
  console.log(greeting);  // 输出 'Hello, World!'
  ```
  
  模板字符串提供了一种更加方便和灵活的方式来创建包含动态内容的字符串。
  
  总之，JavaScript中的字符串是处理文本数据的基本工具，提供了丰富的方法和属性来进行文本操作和处理。
- ## [[JavaScript/regular expression]]