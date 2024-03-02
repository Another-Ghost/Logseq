alias:: CAS, 比较并交换, compare-exchange, 比较交换, 比较交换操作,

- `compare_exchange_strong` 和 `compare_exchange_weak` 是 C++11 引入的两个原子操作，这两个函数尝试以原子方式比较并交换（Compare-And-Swap，CAS）原子对象的值。
- ### 操作原理
	- **操作**：这些函数检查原子对象的当前值是否等于提供的期望值（expected）。如果是，它将原子对象的值更新为新值（desired）。
	- **返回值**：如果成功替换，函数返回 `true`；如果期望值与原子对象的当前值不匹配，函数返回 `false`，**并将 期望值 更新为原子对象的当前值**。
- ### `compare_exchange_strong` vs `compare_exchange_weak`
  
  两者的主要区别在于它们对[[假性失败]]，即在没有明显原因的情况下操作失败 的可能性。
	- **`compare_exchange_strong`**：始终提供精确的比较。如果原子对象的当前值与期望值不相等，操作失败。这个函数不容忍假阳性失败，因此在单次调用中更可靠，但可能在某些架构上性能稍差。
	- **`compare_exchange_weak`**：可能会在没有明显原因的情况下报告失败（即使原子对象的当前值与期望值相等）。这主要是为了在某些处理器架构上提高性能，特别是在循环中使用时。在实际使用中，你通常需要将此操作放在循环中，以保证操作最终成功。
- ### 示例代码
  
  ```cpp
  #include <atomic>
  #include <iostream>
  
  int main() {
    std::atomic<int> value(10);
    int expected = 10;
    if (value.compare_exchange_strong(expected, 20)) {
        std::cout << "Exchange strong succeeded, value is now " << value.load() << std::endl;
    }
  
    expected = 20;
    while (!value.compare_exchange_weak(expected, 30)) {
        // 循环直到成功更新
    }
    std::cout << "Exchange weak succeeded, value is now " << value.load() << std::endl;
  
    return 0;
  }
  ```
- ### 使用建议
	- 当操作不在循环中或者你需要确保每次操作尽可能减少失败时，使用 `compare_exchange_strong`。
	- 当操作在循环中并且对性能有要求时，可以使用 `compare_exchange_weak`，因为它在某些平台上可能更高效。