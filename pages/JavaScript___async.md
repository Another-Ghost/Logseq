- `async` 关键字是用于声明一个异步函数，它使得 JavaScript 函数有能力处理异步操作，更具体地说，它允许函数以异步方式执行操作，而不会阻塞代码的后续执行。使用 `async` 声明的函数会隐式返回一个 `Promise` 对象，可以用 `await` 关键字在函数内部暂停执行，直到等待 Promise 解决（resolved）。
- ### 特点和用法
	- **隐式返回 Promise**：`async` 函数自动将其返回值包装成 `Promise`。如果函数返回非 `Promise` 值，该值会被 `Promise.resolve()` 包装为 `Promise`。
	- **使用 `await`**：在 `async` 函数内部，可以使用 `await` 关键字来等待一个 `Promise` 的解决，这样可以暂停 `async` 函数的执行，直到 `Promise` 完成，然后继续执行函数并返回结果。
	- **错误处理**：`async` 函数中的异常会被转换为拒绝（rejected）的 `Promise`。使用 `try-catch` 语句可以捕获这些异常。
- ### 示例
  下面是一个使用 `async` 和 `await` 的例子：
  ```javascript
  async function asyncFunction() {
    try {
        const result = await someAsyncOperation();  // 等待异步操作完成
        console.log(result);  // 异步操作完成后输出结果
        return 'Operation completed';
    } catch (error) {
        console.error('An error occurred:', error);
        throw error;  // 将错误作为拒绝的Promise抛出
    }
  }
  ```
  在这个例子中：
	- `asyncFunction` 是一个异步函数。
	- `await someAsyncOperation()` 暂停函数执行，直到 `someAsyncOperation()` 返回的 `Promise` 被解决（或拒绝）。
	- 如果 `Promise` 成功解决，`await` 表达式的结果就是 `Promise` 解决时传递的值。
	- 如果 `Promise` 被拒绝，`await` 表达式会抛出拒绝的原因，可以用 `try-catch` 结构来捕获这个错误。
	  因此，`async` 关键字提供了一种更简洁和直观的方式来编写处理异步操作的代码，使得异步代码看起来更像是同步的。