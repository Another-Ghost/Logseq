alias:: arguments, arguments 对象

- 在JavaScript中，`arguments`对象是一个类数组对象，它包含了传递给函数的所有参数。这个对象只在函数体内可用，允许你访问调用函数时传递给它的所有参数。
- ### 特性
- `arguments`提供了对函数参数的完整访问，无论函数声明时定义了多少形参。
- 它类似于数组，但不是真正的数组实例，所以它没有数组的方法，如`push`、`pop`或`slice`。然而，你可以使用`Array.prototype`方法来操作`arguments`对象。
- `arguments`对象的`length`属性表示传递给函数的参数个数。
- ### 使用`arguments`
  
  ```javascript
  function exampleFunction() {
    console.log(arguments.length);  // 输出传递给函数的参数个数
    console.log(arguments[0]);      // 输出第一个参数
    console.log(arguments[1]);      // 输出第二个参数
    // ...
  }
  
  exampleFunction(1, 'string', true);
  ```
  
  在这个例子中，`exampleFunction`调用时传递了三个参数，所以`arguments.length`的值是3，`arguments[0]`、`arguments[1]`和`arguments[2]`分别是1、'string'和true。
- ### `arguments`和箭头函数
  
  在箭头函数中没有`arguments`对象。如果你尝试在箭头函数中访问`arguments`，它会引用到箭头函数外层函数的`arguments`对象。如果箭头函数外层没有普通函数，那么它会引用全局的`arguments`，这通常是不可取的。如果你需要在箭头函数中访问参数列表，可以使用剩余参数（`...args`）来代替。
- ### 使用剩余参数代替`arguments`
  
  ```javascript
  const exampleFunction = (...args) => {
    console.log(args.length);  // 输出传递给函数的参数个数
    console.log(args[0]);      // 输出第一个参数
    console.log(args[1]);      // 输出第二个参数
    // ...
  }
  
  exampleFunction(1, 'string', true);
  ```
  
  在这个例子中，`...args`是一个剩余参数，它会收集所有传递给函数的参数到一个真正的数组中。这样，你就可以在箭头函数中使用数组方法来处理参数了。
  
  总之，`arguments`对象在普通函数中非常有用，它允许你访问传递给函数的所有参数。但在箭头函数中，你应该使用剩余参数来获取函数的参数列表。