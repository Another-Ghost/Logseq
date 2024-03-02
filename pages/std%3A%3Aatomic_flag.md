- `std::atomic_flag` 是 C++11 引入的一个[[原子类型]]，提供了最基本的原子布尔标志。它是标准库中**唯一**保证提供[[无锁]][[原子操作]]的类型，因此它非常适合用作原子状态标志或实现[[自旋锁]]。
- ### 主要特性
	- **无锁性**：`std::atomic_flag` 是真正的无锁原子操作，保证了在多线程环境中的高效执行。
	- **操作简单**：它只支持两种操作：设置（`set`）和清除（`clear`），以及检测并设置（`test-and-set`）。
	- **初始化**：必须使用 `ATOMIC_FLAG_INIT` 宏进行初始化。
- ### 操作
	- **`test_and_set()`**：检查 `std::atomic_flag` 的当前值。如果 `std::atomic_flag` 之前未设置，将其设置为 `true` 并返回 `false`；如果之前已经被设置，则返回 `true`。这个操作是原子的。
	- **`clear()`**：将 `std::atomic_flag` 的值设置为 `false`。这个操作也是原子的。
- ### 基本用法
  ```cpp
  #include <atomic>
  #include <thread>
  #include <vector>
  #include <iostream>
  
  std::atomic_flag lock = ATOMIC_FLAG_INIT;
  
  void f(int n) {
    while (lock.test_and_set(std::memory_order_acquire)) {
        // 等待锁被释放
    }
    std::cout << "Output from thread " << n << '\n';
    lock.clear(std::memory_order_release);
  }
  
  int main() {
    std::vector<std::thread> v;
    for (int n = 0; n < 10; ++n) {
        v.emplace_back(f, n);
    }
    for (auto& t : v) {
        t.join();
    }
    return 0;
  }
  ```
  
  在这个例子中，多个线程尝试进入临界区来打印其ID，`std::atomic_flag` 被用作自旋锁来确保一次只有一个线程可以进入临界区。
- ``` cpp 
  class spinlock_mutex
  {
  	std::atomic_flag flag;
  public:
  	spinlock_mutex():
  		flag(ATOMIC_FLAG_INIT)
  	{}
  	
    	void lock()
  	{
  		while(flag.test_and_set(std::memory_order_acquire));
  	}
  	
    void unlock()
  	{
  		flag.clear(std::memory_order_release);
  	}
  };
  ```
- ### 注意事项
	- `std::atomic_flag` 不能被复制或移动。
	- 使用 `std::atomic_flag` 实现的自旋锁在等待锁释放时会持续占用CPU，因此它更适合实现等待时间非常短的锁。
	- 对于复杂的同步需求，可能需要使用更高级的原子类型或同步原语，如[[std::mutex]]和 [[std::condition_variable]]。
	- 由于 `std::atomic_flag` 的局限性太强，因为没有 *非修改查询操作*（类似 `load`），所以甚至不能像普通的布尔标志那样使用。所以，实际操作中最好使用 [[std::atomic<bool>]] ，接下来让我们看看应该如何使用它。