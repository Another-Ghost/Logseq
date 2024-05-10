- JavaScript中的作用域是指程序中定义变量的区域，这影响了变量的可见性和生命周期。JavaScript主要有两种类型的作用域：全局作用域和函数作用域，ES6引入了块级作用域。理解这些作用域有助于编写更加可靠和维护的代码。
- ### 全局作用域
  
  当一个变量在函数外部被声明时，它就被定义在全局作用域内。全局作用域中的变量在代码的任何地方都可以访问和修改。
  
  ```javascript
  var globalVar = "I am global";
  
  function testScope() {
    console.log(globalVar); // 可以访问全局变量
  }
  
  testScope(); // 输出: I am global
  console.log(globalVar); // 输出: I am global
  ```
  
  全局变量在整个应用生命周期内都存在，容易造成命名冲突，并可能被任何部分的代码改变，这增加了代码的复杂性和不可预测性。
- ### 函数作用域
  
  函数作用域是指在函数内部声明的变量。这些变量只能在该函数内部访问，外部无法访问。
  
  ```javascript
  function testFunctionScope() {
    var functionScopedVar = "I am function scoped";
    console.log(functionScopedVar); // 可以访问
  }
  
  testFunctionScope(); // 输出: I am function scoped
  // console.log(functionScopedVar); // 错误：functionScopedVar 在这里不可见
  ```
  
  函数作用域有助于避免变量名冲突，使得变量只在需要的范围内存在，有助于内存管理。
- ### [[块作用域]]
  
  ES6引入了`let`和`const`关键词，允许创建块级作用域的变量。块级作用域是由最近的一对大括号 `{}` 定义的区域，例如在`if`语句、`for`循环、`while`循环中。
  
  ```javascript
  if (true) {
    let blockScopedVar = "I am block scoped";
    console.log(blockScopedVar); // 可以访问
  }
  
  // console.log(blockScopedVar); // 错误：blockScopedVar 在这里不可见
  ```
  
  块级作用域有助于进一步减少全局命名空间的污染，也使得代码更容易理解。
- ### 作用域链
  
  JavaScript使用词法作用域（也称为静态作用域），意味着函数的作用域在定义时就决定了，而不是在执行时。这导致了作用域链的概念，其中函数内部可以访问其外部作用域中的变量。
  
  ```javascript
  var outerVar = "I am from outer";
  
  function outerFunction() {
    function innerFunction() {
        console.log(outerVar); // 可以访问外部函数的变量
    }
    
    innerFunction();
  }
  
  outerFunction(); // 输出: I am from outer
  ```
  
  在上面的例子中，`innerFunction` 可以访问`outerFunction` 中的`outerVar`，因为`outerVar`在`innerFunction`的外部作用域中。
- ### [[闭包]]
  
  闭包是JavaScript中一个重要的概念，它允许函数记住并访问其词法作用域，即使函数在其词法作用域外执行。这通常通过返回一个函数来实现，这个返回的函数可以访问其定义时的作用域。
  
  ```javascript
  function createFunction() {
    var localToCreateFunction = "I am from createFunction";
  
    return function() {
        console.log(localToCreateFunction);
    };
  }
  
  var myFunction = createFunction();
  myFunction(); // 输出: I am from createFunction
  ```
  
  在这个例子中，即使`createFunction`执行完毕后，返回的函数依然可以访问`localToCreateFunction`
  
  ，因为它是通过闭包保持对其作用域的访问。
- 理解JavaScript的作用域和闭包是编写有效和高效JavaScript代码的基础。这些概念有助于管理变量的可见性和生命周期，避免[[全局变量污染]]，并实现更加模块化和结构化的代码。