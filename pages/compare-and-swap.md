alias:: CAS, 比较并交换, compare-exchange, 比较交换, 比较交换操作, compare-exchange operation

- [[compare_exchange_strong]]和[[compare_exchange_weak]]是 C++11 引入的两个原子操作，这两个函数尝试以原子方式比较并交换（Compare-And-Swap，CAS）原子对象的值。
- ### 操作原理
	- **操作**：这些函数检查原子对象的当前值是否等于提供的^^期望值^^（`expected`）。
		- 如果是，它将原子对象的值更新为^^新值^^（`desired`）；
		- 不是则将**期望值更新**为原子对象（`*this`）的当前值。
			- >如果期望值和内存位置的当前值不一致，说明在执行CAS之前，有其他线程已经修改了该位置的值。
			  更新期望值至原子对象的当前值，是为了保证下一次尝试使用正确的比较基准。这个过程有助于减少无效操作并提高算法的效率，尤其是在忙等待（Busy-waiting）或自旋锁（Spinlock）等策略中，确保每次循环都是基于最新的、有效的状态进行操作。
	- **返回值**：如果成功替换，函数返回 `true`；如果期望值与原子对象的当前值不匹配，函数返回 `false`。
- ### `compare_exchange_strong` vs `compare_exchange_weak`
  两者的主要区别在于它们对[[假性失败]]，即在没有明显原因的情况下操作失败 的可能性。
	- **[[compare_exchange_strong]]**：保证在比较成功的情况下，交换一定会成功。如果比较失败，它会返回`false`。这个函数**不容忍假性失败**，因此，`compare_exchange_strong`通常用于需要一次性确定操作成功或失败的场景。但可能在某些架构上性能稍差。
	- **[[compare_exchange_weak]]**：可能会在比较成功但交换失败的情况下返回`false`，这通常是由于多线程并发操作导致的。因此，当使用`compare_exchange_weak`时，通常需要将其放在一个循环中，以确保交换操作最终成功。这主要是为了在某些处理器架构上提高性能，特别是在循环中使用时。在实际使用中，你通常需要将此操作放在循环中，以保证操作最终成功。
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
- `compare_exchange_weak`和`compare_exchange_strong`都是原子操作，用于比较并交换原子对象的值。它们的主要区别在于对于失败的处理方式。
- 因此，当使用`compare_exchange_weak`时，通常需要将其放在一个循环中，以确保交换操作最终成功。
- ```cpp
  while(!head.compare_exchange_weak(new_node.ptr->next, new_node));
  ```
- `compare_exchange_strong`则保证在比较成功的情况下，交换一定会成功。如果比较失败，它会返回`false`。因此，`compare_exchange_strong`通常用于需要一次性确定操作成功或失败的场景。
- ```cpp
  if(head.compare_exchange_strong(old_head,ptr->next))
  ```
- 在这段代码中，`compare_exchange_weak`用于`push`方法中尝试更新[`head`](command:_github.copilot.openSymbolInFile?%5B%22src%2FReferenceCounting.cpp%22%2C%22head%22%5D "src/ReferenceCounting.cpp")，`compare_exchange_strong`用于`pop`方法中尝试更新[`head`](command:_github.copilot.openSymbolInFile?%5B%22src%2FReferenceCounting.cpp%22%2C%22head%22%5D "src/ReferenceCounting.cpp")。这是因为`push`方法可以容忍失败并重试，而`pop`方法需要在取出元素后立即确定是否成功。
- ### 使用建议
	- 当操作不在循环中或者你需要确保每次操作尽可能减少失败时，使用 `compare_exchange_strong`。
	- 当操作在循环中并且对性能有要求时，可以使用 `compare_exchange_weak`，因为它在某些平台上可能更高效。