- JavaScript中的数组是用来存储多个值的单一变量。数组中的每个值（元素）可以是任意数据类型，包括字符串、数字、布尔值、对象甚至其他数组（这就是所谓的多维数组）。
- ### 创建数组
  
  有几种方式可以创建数组：
  
  1. **使用数组字面量**：
  
   ```javascript
   let fruits = ['Apple', 'Banana', 'Cherry'];
   ```
  
  2. **使用`new Array()`构造函数**：
  
   ```javascript
   let fruits = new Array('Apple', 'Banana', 'Cherry');
   ```
  
  数组字面量是创建数组的更常见和推荐的方式。
- ### 访问数组元素
  
  你可以通过索引（位置）来访问数组中的元素，索引从0开始：
  
  ```javascript
  let firstFruit = fruits[0];  // Apple
  ```
- ### 修改数组元素
  
  通过索引，你也可以修改数组中的元素：
  
  ```javascript
  fruits[1] = 'Blackberry';  // 将第二个元素更改为 'Blackberry'
  ```
- ### 数组属性和方法
  数组有许多内置的属性和方法来帮助你操作数组：
	- ### 1. 遍历数组
	- `forEach()`: 遍历数组的每个元素，并对每个元素执行回调函数。
	  
	  ```javascript
	  [1, 2, 3].forEach((element, index) => {
	    console.log(`Element at ${index}: ${element}`);
	  });
	  ```
	- ### 2. 转换数组
	- `map()`: 创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后的返回值。
	  
	  ```javascript
	  let squares = [1, 2, 3].map(num => num * num);
	  console.log(squares); // 输出: [1, 4, 9]
	  ```
	- `filter()`: 创建一个新数组，包含通过所提供函数实现的测试的所有元素。
	  
	  ```javascript
	  let evens = [1, 2, 3, 4, 5].filter(num => num % 2 === 0);
	  console.log(evens); // 输出: [2, 4]
	  ```
	- `reduce()`: 对数组中的每个元素执行一个由您提供的 reducer 函数(升序执行)，将其结果汇总为单个返回值。
	  
	  ```javascript
	  let sum = [1, 2, 3].reduce((accumulator, current) => accumulator + current, 0);
	  console.log(sum); // 输出: 6
	  ```
	- ### 3. 搜索数组
	- `find()`: 返回数组中满足提供的测试函数的第一个元素的值，否则返回 `undefined`。
	  
	  ```javascript
	  let found = [1, 2, 3].find(element => element > 2);
	  console.log(found); // 输出: 3
	  ```
	- `includes()`: 判断数组是否包含一个指定的值，根据情况返回 `true` 或 `false`。
	  
	  ```javascript
	  let hasTwo = [1, 2, 3].includes(2);
	  console.log(hasTwo); // 输出: true
	  ```
	- ### 4. 判断函数
	- `every()`: 检测数组所有元素是否都符合指定条件（由函数提供）。
	  
	  ```javascript
	  let allEven = [2, 4, 6].every(num => num % 2 === 0);
	  console.log(allEven); // 输出: true
	  ```
	- `some()`: 检测数组中的某些元素是否符合指定条件（由函数提供）。
	  
	  ```javascript
	  let hasNegative = [1, 2, 3, -1, 4].some(num => num < 0);
	  console.log(hasNegative); // 输出: true
	  ```
	- ### 5. 排序和颠倒元素
	- `sort()`: 对数组的元素进行排序。
	  
	  ```javascript
	  let numbers = [3, 1, 4, 1, 5, 9];
	  numbers.sort((a, b) => a - b);
	  console.log(numbers); // 输出: [1, 1, 3, 4, 5, 9]
	  ```
	- `reverse()`: 颠倒数组中元素的顺序。
	  
	  ```javascript
	  let array = [1, 2, 3];
	  array.reverse();
	  console.log(array); // 输出: [3, 2, 1]
	  ```
	- ### 6. 切片和拼接
	- `slice()`: 返回数组的一部分浅拷贝到一个新数组对象。
	  
	  ```javascript
	  let numbers = [1, 2, 3, 4, 5];
	  let sliced = numbers.slice(1, 3);
	  console.log(sliced); // 输出: [2, 3]
	  ```
	- `concat()`: 用于合并两个或多个数组，不会改变现有的数组，而是返回一个新数组。
	  
	  ```javascript
	  let first = [1, 2, 3];
	  let second = [4, 5, 6];
	  let combined = first.concat(second
	  
	  );
	  console.log(combined); // 输出: [1, 2, 3, 4, 5, 6]
	  ```
	- ### 7. 添加或删除元素
	- `push()`: 向数组的末尾添加一个或多个元素，并返回新的长度。
	  
	  ```javascript
	  let fruits = ['apple', 'banana'];
	  fruits.push('orange');
	  console.log(fruits); // 输出: ['apple', 'banana', 'orange']
	  ```
	- `pop()`: 删除数组的最后一个元素，并返回该元素。
	  
	  ```javascript
	  let numbers = [1, 2, 3];
	  let last = numbers.pop();
	  console.log(last); // 输出: 3
	  console.log(numbers); // 输出: [1, 2]
	  ```
	- `shift()`: 删除数组的第一个元素，并返回该元素。
	  
	  ```javascript
	  let numbers = [1, 2, 3];
	  let first = numbers.shift();
	  console.log(first); // 输出: 1
	  console.log(numbers); // 输出: [2, 3]
	  ```
	- `unshift()`: 向数组的开头添加一个或多个元素，并返回新的长度。
	  
	  ```javascript
	  let numbers = [2, 3];
	  numbers.unshift(1);
	  console.log(numbers); // 输出: [1, 2, 3]
	  ```
	- ### 8. 数组拼接和填充
	- `join()`: 将数组中的所有元素连接成一个字符串。
	  
	  ```javascript
	  let elements = ['Fire', 'Air', 'Water'];
	  let result = elements.join();
	  console.log(result); // 输出: "Fire,Air,Water"
	  ```
	- `fill()`: 用一个固定值填充数组中从起始索引到终止索引内的全部元素。
	  
	  ```javascript
	  let array = [1, 2, 3, 4];
	  array.fill(0, 2, 4);
	  console.log(array); // 输出: [1, 2, 0, 0]
	  ```
	- ### 9. 数组变换
	- `flatMap()`: 首先使用映射函数映射每个元素，然后将结果压平一层。
	  
	  ```javascript
	  let array = [1, 2, 3, 4];
	  let mappedAndFlattened = array.flatMap(x => [x, x * 2]);
	  console.log(mappedAndFlattened); // 输出: [1, 2, 2, 4, 3, 6, 4, 8]
	  ```
	- `flat()`: 按照指定深度递归遍历数组，并将所有元素与遍历到的子数组元素合并为一个新数组返回。
	  
	  ```javascript
	  let nestedArray = [1, [2, 3], [4, [5, 6]]];
	  let flattenedArray = nestedArray.flat(2);
	  console.log(flattenedArray); // 输出: [1, 2, 3, 4, 5, 6]
	  ```
	- ### 10. 数组查找
	- `indexOf()`: 返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回 -1。
	  
	  ```javascript
	  let fruits = ['apple', 'banana', 'orange'];
	  let index = fruits.indexOf('banana');
	  console.log(index); // 输出: 1
	  ```
	- `lastIndexOf()`: 返回在数组中可以找到一个给定元素的最后一个索引，如果不存在，则返回 -1。
	  
	  ```javascript
	  let numbers = [1, 2, 3, 2, 1];
	  let lastIndex = numbers.lastIndexOf(2);
	  console.log(lastIndex); // 输出: 3
	  ```
	- `findIndex()`: 返回数组中满足提供的测试函数的第一个元素的索引。否则返回 -1。
	  
	  ```javascript
	  let numbers = [1, 5, 10, 15];
	  let index = numbers.findIndex(number => number > 9);
	  console.log(index); // 输出: 2
	  ```
	- ### 11. 检测数组
	- `Array.isArray()`: 用于确定传递的值是否是一个 `Array`。
	  
	  ```javascript
	  console.log(Array.isArray([1, 2, 3]));  // 输出: true
	  console.log(Array.isArray({foo: 123})); // 输出: false
	  ```
	- ### 12. 迭代方法
	- `keys()`: 返回一个包含数组中每个索引键的新 `Array Iterator` 对象。
	  
	  ```javascript
	  let array = ['a', 'b', 'c'];
	  let iterator = array.keys();
	  for (let key of iterator) {
	    console.log(key); // 输出: 0 1 2
	  }
	  ```
	- `values()`: 返回一个新的 `Array Iterator` 对象，包含数组每个索引的值。
	  
	  ```javascript
	  let array = ['a', 'b', 'c'];
	  let iterator = array.values();
	  for (let value of iterator) {
	    console.log(value); // 输出: 'a' 'b' 'c'
	  }
	  ```
	- `entries()`: 返回一个新的 `Array Iterator` 对象，它包含数组中每个索引的键/值对。
	  
	  ```javascript
	  let array = ['a', 'b', 'c'];
	  let iterator = array.entries();
	  for (let entry of iterator) {
	    console.log(entry); // 输出: [0, 'a'] [1, 'b'] [2, 'c']
	  }
	  ```
	- ### 13. 数组缓冲区
	- `buffer` 和 `byteLength`: 对于类型化数组来说，这些属性提供了底层二进制数据缓冲区的信息。
	  
	  ```javascript
	  let typedArray = new Uint8Array([1, 2, 3]);
	  console.log(typedArray.buffer);    // 输出: ArrayBuffer {...}
	  console.log(typedArray.byteLength); // 输出: 3
	  ```
	- ### 14. 数组的静态方法
	- `Array.from()`: 从类数组或可迭代对象中创建一个新的数组实例。
	  
	  ```javascript
	  console.log(Array.from('foo')); // 输出: ['f', 'o', 'o']
	  ```
	- `Array.of()`: 创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。
	  
	  ```javascript
	  console.log(Array.of(1, 2, 3)); // 输出: [1, 2, 3]
	  ```
	- ### 15. 其他方法
	- `copyWithin()`: 在数组内部，将一系列元素从一个位置复制到另一个位置，并返回它，不会改变数组的长度。
	  
	  ```javascript
	  console.log([1, 2, 3, 4, 5].copyWithin(0, 3)); // 输出: [4, 5, 3, 4, 5]
	  ```
	- `toLocaleString()`: 返回一个字符串表示数组中的元素。元素通过各自的 `toLocaleString` 方法转换成字符串。
	  
	  ```javascript
	  let number = 1337;
	  let date = new Date();
	  console.log([number, date].toLocaleString()); // 输出: '1,337, MM/DD/YYYY, HH:MM:SS AM/PM'
	  ```
	- `toString()`: 返回一个由数组中的所有元素转换成字符串并通过逗号分隔连接起来的字符串。
	  
	  ```javascript
	  console.log([1, 2, 'a', '1a'].toString()); // 输出: '1,2,a,1a'
	  ```
	  
	  这些方法进一步扩展了 JavaScript 数组的功能，使得它们可以处理更多类型的数据和更复杂的数据结构操作。