alias:: 原子读-修改-写操作, RMW operation, read-modify-write, 读-修改-写操作, RMW

- 读-修改-写操作（Read-Modify-Write, RMW）是一种原子操作，主要用于并发编程和多线程环境中，以确保多个线程之间的数据一致性和同步。RMW 操作的核心在于原子性，它可以确保整个操作在没有其他线程干预的情况下完成，从而避免竞态条件和数据竞争。
- ### 读-修改-写操作的原理
  RMW 操作通常涉及以下几个步骤：
	- **读取数据**：从共享变量中读取当前值。
	  logseq.order-list-type:: number
	- **修改数据**：根据需求修改读取到的值。
	  logseq.order-list-type:: number
	- **写入数据**：将修改后的值写回到共享变量。
	  logseq.order-list-type:: number
	- 这三个步骤必须在原子性上下文中完成，以确保在操作过程中没有其他线程可以插入或干预。这种原子性是防止数据竞争的关键。
- ### C++ 中的读-修改-写操作
  在 C++ 中，RMW 操作可以通过 `std::atomic` 类及其相关的方法实现，这些方法提供了原子性和内存排序的支持。常见的 RMW 操作包括：
	- [[fetch_add()]]：原子性地读取、增加并写回值。
	- fetch_sub()：原子性地读取、减少并写回值。
	- [[compare_exchange_weak()]] 和 [[compare_exchange_strong()]]：原子性地比较并交换值。
	  
	  ```cpp
	  #include <atomic>
	  #include <iostream>
	  
	  std::atomic<int> counter(0);
	  
	  void increment() {
	  counter.fetch_add(1, std::memory_order_relaxed);
	  }
	  
	  void decrement() {
	  counter.fetch_sub(1, std::memory_order_relaxed);
	  }
	  
	  int main() {
	  increment();
	  decrement();
	  std::cout << "Counter: " << counter.load() << std::endl;
	  return 0;
	  }
	  ```
	  
	  在这个例子中，`fetch_add()` 和 `fetch_sub()` 是典型的读-修改-写操作，确保多个线程对共享变量的操作是原子性的。