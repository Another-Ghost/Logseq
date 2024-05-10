- 在JavaScript中，嵌套函数是指定义在另一个函数内部的函数。这种结构允许内部函数访问外部函数的变量和参数，这是通过词法作用域和闭包的概念来实现的。
- ### [[词法作用域]]
  词法作用域意味着函数的作用域在函数定义时就已经确定，而不是在执行时确定。因此，嵌套函数可以访问在其外部函数中定义的变量。
- ### 示例
  下面是一个嵌套函数的示例：
  ```javascript
  function outerFunction() {
    let outerVar = 'I am from the outer function';
  
    function innerFunction() {
        console.log(outerVar);
    }
  
    innerFunction();
  }
  
  outerFunction();  // 输出: I am from the outer function
  ```
  
  在这个例子中，`innerFunction`是在`outerFunction`内部定义的。`innerFunction`可以访问`outerFunction`中定义的变量`outerVar`。
- ### [[闭包]]
  嵌套函数可以形成闭包。闭包是指那些能够访问[[自由变量]]的函数，其中^^自由变量^^是指在函数体中使用的，但既不是函数参数也不是函数的局部变量的变量。
  闭包的一个常见用途是创建具有私有变量的函数。这些变量不能从外部直接访问，只能通过**闭包提供的函数**来访问或修改。
  ```javascript
  function createCounter() {
    let count = 0;
  
    return {
        increment: function() {
            count++;
            console.log(count);
        },
        decrement: function() {
            count--;
            console.log(count);
        }
    };
  }
  
  const counter = createCounter();
  counter.increment();  // 输出: 1
  counter.increment();  // 输出: 2
  counter.decrement();  // 输出: 1
  ```
  
  在这个例子中，`createCounter`函数返回一个包含两个方法（`increment`和`decrement`）的对象。这两个方法都是闭包，它们共享相同的环境，即`createCounter`函数的作用域。因此，它们可以访问和修改`count`变量，而这个变量对于外部代码来说是私有的。
- ### 总结
  
  嵌套函数和闭包是JavaScript中非常强大的特性，它们允许你：
- 封装和组织代码。
- 创建模块化和可重用的代码块。
- 实现数据封装和信息隐藏。
  
  通过这些特性，你可以编写更加清晰、可维护和高效的JavaScript代码。