alias:: 箭头函数

- 箭头函数是ES6中引入的一种新的函数写法，它提供了一种更简洁的方式来编写函数表达式。箭头函数有几个特点和优势：
- ### 语法
  箭头函数的基本语法如下：
  ```javascript
  const functionName = (参数1, 参数2, ..., 参数N) => {
    // 函数体
  }
  ```
  如果箭头函数只有一个参数，可以省略参数周围的括号：
  ```javascript
  const functionName = 参数 => {
    // 函数体
  }
  ```
  如果函数体只包含一个表达式，可以省略花括号，并且该表达式的结果会自动返回：
  ```javascript
  const functionName = 参数 => 表达式;
  ```
- ### 特点
  
  1. **没有自己的`this`**：箭头函数不绑定自己的`this`，它会捕获其所在上下文的`this`值作为自己的`this`值，这使得`this`在函数内外保持一致，特别适合用在回调函数中。
  
  2. **没有[[arguments]]对象**：箭头函数没有自己的`arguments`对象，但是可以访问外围函数的`arguments`对象。
  
  3. **不能用作构造函数**：箭头函数不能使用`new`关键字，因为箭头函数没有自己的`this`，也没有`prototype`属性，所以不能将其作为构造函数使用。
  
  4. **没有`prototype`属性**：由于不能用作构造函数，箭头函数没有`prototype`属性。
  
  5. **不能用作生成器函数**：箭头函数不能使用`yield`关键字，在箭头函数中使用`yield`会导致语法错误。
- ### 示例
  下面是一些箭头函数的示例：
  ```javascript
  // 无参数的箭头函数
  const sayHello = () => console.log('Hello!');
  
  // 单个参数的箭头函数
  const square = x => x * x;
  
  // 多个参数的箭头函数
  const add = (a, b) => a + b;
  
  // 多行表达式的箭头函数
  const sortArray = array => {
    return array.sort((a, b) => a - b);
  };
  
  // 立即执行的箭头函数
  ((name) => console.log(`Hello, ${name}!`))('World');
  ```
  
  箭头函数因其简洁性和`this`行为而广受欢迎，特别是在需要定义快速执行的小函数或需要确保`this`上下文不变的情况下（如事件处理器、定时器、Promise处理等）。