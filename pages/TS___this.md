- 在 TypeScript 中，`this` 关键字在类的方法中使用，代表调用该方法的对象实例。这是一个基本示例：
- ```typescript
  class MyClass {
    myProperty: string;
    constructor() {
        this.myProperty = "Hello";
    }
    myMethod() {
        console.log(this.myProperty); // 输出 "Hello"
    }
  }
  ```