alias:: compare_exchange_strong

- ``` cpp
  bool compare_exchange_strong( T& expected, T desired,
                                std::memory_order success,
                                std::memory_order failure ) noexcept;
  bool compare_exchange_strong( T& expected, T desired,
                                std::memory_order order =
                                    std::memory_order_seq_cst ) noexcept;
  ```
- `compare_exchange_strong`是一个原子操作，它检查`*this`的值是否仍然是`expected`（即有没有其他线程修改过`*this`）：
	- 如果是（说明`*this`没有被修改），就将`*this`更新为`disired`，然后返回 `true`。
	- 如果不是（说明其他线程已经修改了`*this`），先将`*this`的当前值同步给`expected`，然后返回`false`。
- 见 [[compare-and-swap]]。
-