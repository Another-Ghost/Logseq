alias:: compare_exchange_weak

- ``` cpp
  bool compare_exchange_weak( T& expected, T desired,
                              std::memory_order success,
                              std::memory_order failure ) noexcept;
  bool compare_exchange_weak( T& expected, T desired,
                              std::memory_order order =
                                  std::memory_order_seq_cst ) noexcept;
  ```
- 见 [[compare-and-swap]]。