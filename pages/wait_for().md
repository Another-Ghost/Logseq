alias:: wait_for

- `std::future::wait_for` 是 C++ 中用于等待 `std::future` 对象关联的异步操作完成的成员函数之一。它允许程序在特定的时间点等待异步操作的完成，以便获取异步操作的结果或执行后续的操作。
- ### 函数签名
  ```cpp
  template <class Rep, class Period>
  std::future_status wait_for(const std::chrono::duration<Rep, Period>& timeout_duration) const;
  
  void wait() const;
  ```
- ### 参数
	- `timeout_duration`：等待的时间段，类型为 `std::chrono::duration`，表示等待的最长时间。如果异步操作在指定的时间段内未完成，则等待操作将返回，并且返回值为 `std::future_status::timeout`。
- ### 返回值
	- `wait_for` 函数返回一个枚举值 `std::future_status`，表示等待的状态，可能为以下值之一：
		- `std::future_status::ready`：异步操作已经完成。
		- `std::future_status::timeout`：等待超时。
		- `std::future_status::deferred`：异步操作被推迟，等待 `get` 调用时执行。
	- `wait` 函数无返回值。