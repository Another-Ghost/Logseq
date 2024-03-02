alias:: 假性失败, 假失败

- 假性失败（Spurious Failure）在并发编程中是指某些操作在没有明显的失败原因下报告失败的情况。这一术语通常与原子操作中的“比较并交换”（Compare-And-Swap，CAS）操作相关联，尤其是在讨论 `compare_exchange_weak` 函数时。
- ### 假性失败的背景
  
  `compare_exchange_weak` 是一种CAS操作，它尝试将某个原子变量的值与一个给定的期望值进行比较，如果相等，则将该变量的值更新为新值。然而，即使原子变量的当前值与期望值相等，`compare_exchange_weak` 也可能因为假性失败而报告操作失败。这种行为主要是为了在某些处理器架构上提高性能，例如在处理器需要处理某些低级别竞争或中断时。
- ### 假性失败的影响
- **性能优化**：在某些场景下，接受假性失败可以使硬件和编译器生成更高效的代码。例如，**在循环中使用 `compare_exchange_weak` 可能会比 `compare_exchange_strong` 更高效**，尤其是在那些对CAS操作进行优化的处理器架构上。
- **编程模型**：开发者需要在使用 `compare_exchange_weak` 时准备好处理假性失败，通常通过将操作放置在循环中来不断重试，直到成功为止。
- ### 示例：处理假性失败
  
  ```cpp
  #include <atomic>
  #include <iostream>
  
  int main() {
    std::atomic<int> value(10);
    int expected = 10;
    while (!value.compare_exchange_weak(expected, 20)) {
        // 操作失败，expected 被更新为value的当前值
        // 在循环中重试，直到成功为止
    }
    std::cout << "Value successfully changed to " << value.load() << std::endl;
    return 0;
  }
  ```
  
  在这个例子中，即使发生假性失败，循环也会持续尝试更新`value`直到`compare_exchange_weak`操作成功。
- ### 最佳实践
	- 在可能经历假性失败的场景下使用 `compare_exchange_weak`，并将其放置在循环中以确保最终成功。
	- 考虑使用 `compare_exchange_strong` 作为替代，如果你需要避免假性失败或者在不支持或不优化 `compare_exchange_weak` 的架构上工作。
	- 明确你的并发需求和性能目标，选择最合适的原子操作和内存顺序模型。