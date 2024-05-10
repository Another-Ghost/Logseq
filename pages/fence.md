alias:: 栅栏, memory barrier, 内存栅栏

- 没有栅栏（Fences）的 *原子操作库* 将是不完整的。这些是在不修改任何数据的情况下强制执行[[内存排序约束]]的操作，通常与使用[[memory_order_relaxed]]排序约束的原子操作结合使用。栅栏是 *全局操作* ，影响执行栅栏的线程中其他原子操作的排序。栅栏也常被称为 memory barrier ，之所以这样命名，是因为它们在代码中设定了一条某些操作不能跨越的线。
  对不同变量的宽松操作通常可以由编译器或硬件自由重排序。栅栏限制了这种自由，并引入了之前不存在的[[happens-before]]和[[synchronizes-with]]关系。
- ## 示例
  下面清单中的每个线程上的两个原子操作之间添加了一个栅栏：
  ``` cpp
  /*栅栏可以让宽松操作变的有序*/
  #include <atomic>
  #include <thread>
  #include <assert.h>
  std::atomic<bool> x,y;
  std::atomic<int> z;
  void write_x_then_y()
  {
      x.store(true,std::memory_order_relaxed); // 1
      std::atomic_thread_fence(std::memory_order_release); // 2
      y.store(true,std::memory_order_relaxed); // 3
  }
  void read_y_then_x()
  {
      while(!y.load(std::memory_order_relaxed)); // 4
      std::atomic_thread_fence(std::memory_order_acquire); // 5
      if(x.load(std::memory_order_relaxed)) // 6
      	++z;
  }
  int main()
  {
      x=false;
      y=false;
      z=0;
      std::thread a(write_x_then_y);
      std::thread b(read_y_then_x);
      a.join();
      b.join();
      assert(z.load()!=0); // 7
  }
  ```
  释放栅栏 2 与 获取栅栏 5 同步，因为在 4 处对 y 的加载读取了在 3 处存储的值。这意味着在 1 处对 x 的存储发生在 6 处对 x 的加载之前，所以读取的值必须是 true ，而在 7 处的断言不会触发。
  这与没有栅栏的原始情况形成对比，在那种情况下，对 x 的存储和从 x 的加载没有被排序，因此断言可能会触发。
  注意，**两个栅栏都是必需的：你需要在一个线程中有一个释放，在另一个线程中有一个获取，以获得一个[[synchronizes-with 关系]]。
  在这种情况下，释放栅栏 2 的效果就如同对 y 的存储 3 被标记为`memory_order_release`而不是`memory_order_relaxed`。同样，获取栅栏 5 使得从y的加载 4 就好像被标记为`memory_order_acquire`(都是作用于后一句代码)。
- 这就是栅栏的一般概念：
	- 如果一个[[获取操作]]看到了在释放栅栏之后发生的存储的结果，那么栅栏就与那个获取操作同步；
	  id:: 65e4b7bf-216e-4421-b8ce-79d99db0fdfa
	- 如果在获取栅栏之前发生的加载看到了[[释放操作]]的结果，那么释放操作就与获取栅栏同步。
	- 你可以在两边都有栅栏，就像这里的例子一样，在这种情况下，如果在获取栅栏之前发生的加载看到了在释放栅栏之后发生的存储写入的值，那么释放栅栏就与获取栅栏同步。
	- >尽管栅栏同步依赖于栅栏前后操作读取或写入的值，但重要的是要注意同步点是栅栏本身。如果你从清单中取出 write_x_then_y ，并且按照下面的方式将对 x 的写入移动到栅栏之后，即使对 x 的写入发生在对 y 的写入之前，断言中的条件也不再保证为真：
	  ``` cpp
	  void write_x_then_y()
	  std::atomic_thread_fence(std::memory_order_release);
	  x.store(true,std::memory_order_relaxed);
	  y.store(true,std::memory_order_relaxed);
	  }
	  ```
	  这两个操作不再被栅栏分隔，因此不再有序。只有当栅栏位于对 x 的存储和对 y 的存储之间时，它才强加一个排序。栅栏的存在或缺失不影响因其他原子操作而存在的happens-before关系上的任何强制排序。
- ## 使用原子操作对[[非原子操作]]排序
	- 到目前为止本章中几乎所有其他例子，完全是由具有原子类型的变量构建的。但是，使用原子操作强制排序的真正好处是它们可以在[[非原子操作]]上[[强制排序]]，并避免数据竞争导致的未定义行为。
	- 如果你将上述清单中的 x 替换为普通的 非原子 bool（如下面的清单所示），保证行为是相同的。
	  ``` cpp
	  #include <atomic>
	  #include <thread>
	  #include <assert.h>
	  bool x=false; // x现在是一个非原子变量
	  std::atomic<bool> y;
	  std::atomic<int> z;
	  void write_x_then_y()
	  {
	      x=true; // 1 在栅栏前存储x
	      std::atomic_thread_fence(std::memory_order_release);
	      y.store(true,std::memory_order_relaxed); // 2 在栅栏后存储y
	  }
	  void read_y_then_x()
	  {
	      while(!y.load(std::memory_order_relaxed)); // 3 在#2写入前，持续等待
	      std::atomic_thread_fence(std::memory_order_acquire);
	      if(x) // 4 这里读取到的值，是#1中写入
	      	++z;
	  }
	  int main()
	  {
	      x=false;
	      y=false;
	      z=0;
	      std::thread a(write_x_then_y);
	      std::thread b(read_y_then_x);
	      a.join();
	      b.join();
	      assert(z.load()!=0); // 5 断言将不会触发
	  }
	  ```
	  栅栏仍然提供了对 x 的存储 1 和对 y 的存储 2，以及对y的加载 2 和对x的加载 4 的强制排序，并且对 x 的存储和对 x 的加载之间仍然存在一个 happens-before 关系，所以断言 5 仍然不会触发。
	  对 2 的存储和对 y 的加载 3 仍然必须是原子的；否则，y 上会有数据竞争，但栅栏在读取线程看到 y 的存储值后，对 x 上的操作强制排序。这种[[强制排序]]意味着尽管 x 被一个线程修改并由另一个线程读取，但x上没有数据竞争。
	- 不仅仅是栅栏可以对非原子操作进行排序。使用`memory_order_release/memory_order_consume` 等也可以，本章中的许多例子都可以重写，将一些内存排序宽松操作替换为普通的非原子操作。
- ## [[非原子操作排序]]