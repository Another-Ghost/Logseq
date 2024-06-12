alias:: 结构化的类型系统

- TypeScript 的一个核心原则是类型检查基于对象的属性和行为（type checking focuses on the *shape* that values have）。这有时被叫做“鸭子类型”或“结构类型”（structural typing）。
- 在结构化的类型系统当中，如果两个对象具有相同的结构，则认为它们是相同类型的。
- ```javascript
  interface Point {
    x: number;
    y: number;
  }
   
  function logPoint(p: Point) {
    console.log(`${p.x}, ${p.y}`);
  }
   
  // 打印 "12, 26"
  const point = { x: 12, y: 26 };
  logPoint(point);
  ```