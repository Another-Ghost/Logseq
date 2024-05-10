alias:: 先行, happens-before relationship, happens-before 关系

- ### 先发生关系
  无论线程如何，如果满足以下条件之一，则[[evaluation]] `A` ^^happens-before^^ evaluation `B`：
	- `A` [[sequenced-before]] `B`。
	  logseq.order-list-type:: number
	- `A` [[inter-thread happens before]] `B`。
	  logseq.order-list-type:: number
	- >实现需要确保先发生关系是无环的，如果必要的话可以通过引入额外的同步来确保（这通常只有在涉及 consume operation 时才有必要）。
- 如果一个评估修改了内存位置，而另一个读取或修改了相同的内存位置，并且至少其中一个评估不是原子操作，那么如果这两个评估之间不存在先发生关系，程序的行为是未定义的（程序发生数据竞争）。
- ## 分类
	- 在并发编程中，"happens-before"关系是确保内存操作顺序和可见性的关键概念。这种关系可以分为几种类型，以适应不同的同步需求和场景。以下是"happens-before"关系的一些主要分类：
		- ### [[程序顺序规则]]（Program Order Rule）
		  这是最基本的"happens-before"关系，它指的是在[[同一线程]]中，按照程序代码顺序，一个操作发生在另一个操作之前。这确保了单线程内的操作顺序性和可见性。
		- ### [[synchronizes-with 关系]]
		  "synchronizes-with" 关系是一种**特定类型**的 "happens-before" 关系，它直接关联了**两个具体的操作**。这种关系通常是通过同步原语（如互斥锁、条件变量、原子操作的特定内存顺序）来建立的。当一个操作通过某种同步机制（如释放一个锁）"synchronizes-with" 另一个操作（如随后获取同一个锁），第一个操作对内存的修改对执行第二个操作的线程是可见的。
		- ### 中断规则（Interruption Rule）
		  当一个线程向另一个线程发送中断请求，并且该请求被接收时，发送中断之前的所有操作happens-before中断被接收之后的操作。
		- ### 顺序一致性规则（Sequentially Consistent Rule）
		  对于标记为`memory_order_seq_cst`的原子操作，所有线程看到的操作顺序是一致的。这意味着这些操作之间存在一个全局的顺序，所有线程都必须遵守这个顺序，使得操作在所有线程中看起来是顺序发生的。
		- ### **线程启动规则**（Thread Start Rule）：
			- 在一个线程中启动另一个线程（`Thread.start()`或`std::thread`的构造）happens-before该线程的任何操作。
		- ### **线程终止规则**（Thread Termination Rule）：
			- 线程中的所有操作happens-before对该线程的终止检测（通过`Thread.join()`([[std::thread::join()]])或检查线程状态）。
		- ### **终结器规则**（Finalizer Rule）：
			- 对象构造完成happens-before它的终结器（Finalizer）的开始。
		- ### **传递性**（Transitivity）：
			- 如果A happens-before B，且B happens-before C，那么A happens-before C。
		- ### 跨线程 happens-before 关系（Inter-Thread Happens-Before）
		  这是一个更广泛的概念，指的是任何能够确保一个线程中操作对另一个线程可见的关系。它包括了上述所有规则，并且是理解并发程序中内存操作顺序的基础。
	- ### 应用和重要性
	  
	  正确理解和应用这些"happens-before"关系对于编写正确、高效的并发程序至关重要。它们帮助开发者避免数据竞争和非确定性行为，确保程序的行为符合预期。选择合适的同步机制和内存顺序标志，可以在保证程序正确性的同时，优化性能和资源利用率。
- ## 示例
  
  考虑以下简化的示例，使用 `std::atomic` 和内存顺序标志来建立 happens-before 关系：
  ```cpp
  #include <atomic>
  #include <thread>
  #include <assert.h>
  
  std::atomic<bool> ready(false);
  int data = 0;
  
  void producer() {
    data = 42; // 设置数据
    ready.store(true, std::memory_order_release); // 发布数据，建立 happens-before 关系
  }
  
  void consumer() {
    while (!ready.load(std::memory_order_acquire)); // 等待数据准备好
    assert(data == 42); // 此时，data 的修改对消费者是可见的
  }
  
  int main() {
    std::thread t1(producer);
    std::thread t2(consumer);
  
    t1.join();
    t2.join();
  
    return 0;
  }
  ```
  
  在这个例子中，`producer` 线程中的 `ready.store` 操作 happens-before `consumer` 线程中的 `ready.load` 操作。这确保了 `consumer` 线程能够安全地看到 `data` 变量的修改。
- ### Happens-Before 关系的重要性
	- **保证[[内存可见性]]**：确保在一个线程中对[[共享变量]]所做的修改，对于在**后续操作**中访问该变量的其他线程是可见的。
	- **防止[[重排序]]**：编译器和处理器可能会出于性能优化的目的对指令进行重排序。Happens-before 关系限制了这种重排序，确保必要的[[内存操作顺序]]得以保持，从而维护程序逻辑的正确性。
- ### 避免过度同步
  虽然 happens-before 关系是确保并发程序正确性的基础，但过度同步会降低程序性能。开发者应该仔细分析并发模型，只在必要时建立 happens-before 关系，避免不必要的性能开销。
	- **最小化锁的使用**：尽可能减少锁的使用范围和持有时间，或者使用更细粒度的锁策略。
	- **选择合适的内存顺序**：对于原子操作，使用比顺序一致性更宽松的内存顺序（如 `std::memory_order_acquire` 和 `std::memory_order_release`），在不影响程序正确性的前提下提高性能。
- ### 工具和技术支持
  利用现代编程语言和工具提供的支持来帮助理解和实施 happens-before 关系：
	- **语言支持**：C++11 及更高版本通过 `<atomic>` 和 `<thread>` 等库提供了原子操作和线程同步机制，帮助开发者建立和管理 happens-before 关系。
	- **静态分析工具**：使用[[静态分析工具]]检测并发错误，如数据竞争。这些工具可以帮助发现代码中违反 happens-before 关系的潜在问题。
	- **动态分析工具**：[[动态分析工具]]，如 ThreadSanitizer，能够在运行时检测数据竞争和其他并发问题，是验证 happens-before 关系正确实施的有力辅助。
-
- "happens-before"和[[strongly-happens-before]]关系是程序操作排序的基础构建块；它指定了哪些操作能看到其他操作的效果。
- ### 单个线程内的 Happens-Before
	- 对于[[单个线程]]来说，这基本上是直截了当的：如果一个操作在另一个操作之前顺序执行，那么它也happens-before它，并且[[strongly-happens-before]]它。这意味着如果一个操作（A）在源代码中的一个语句中出现在另一个操作（B）之前，那么A happens-before B，并且A [[strongly-happens-before]] B。
	- 如果操作出现在同一个语句中，通常它们之间没有happens-before关系，因为它们是无序的。这是另一种说法，即排序是未指定的。你知道下面的程序将输出"1,2"或"2,1"，但是具体哪个是未指定的，因为两次对get_num（）的调用顺序是未指定的。
	  在某些情况下，单个语句中的操作是有顺序的，例如使用内置的逗号操作符或一个表达式的结果用作另一个表达式的参数时。但通常，单个语句中的操作是非顺序的，它们之间没有顺序前（因此没有happens-before）关系。一个语句中的所有操作都happens-before下一个语句中的所有操作。
- ### 线程间的 Happens-Before
	- 如果一个线程上的操作 A inter-thread happens-before 另一个线程上的操作 B ，那么A happens-before B。这增加了一个新的关系（[[inter-thread happens-before]]），这是编写多线程代码时的一个重要关系。
	- 在基本层面上，inter-thread happens-before 相对简单，依赖于 synchronizes-with 关系：如果一个线程中的操作 A 与另一个线程中的操作 B [[同步发生]]，那么A [[inter-thread happens-before]] B。它也是一个 *传递关系* ：如果A inter-thread happens-before B，且B inter-thread happens-before C，那么A inter-thread happens-before C。
	- Inter-thread happens-before 还与[[sequenced-before 关系]]结合：如果操作A [[sequenced-before]]操作B，且操作B [[inter-thread happens-before]] 操作C，那么A inter-thread happens-before C。同样，如果A [[synchronizes-with]] B，并且B [[sequenced-before]] C ，那么A [[inter-thread happens-before]] C。这两者 结合意味着，**如果你在单个线程中进行一系列更改，你只需要一个[[synchronizes-with 关系]]，数据就对执行 C 的线程上的后续操作[[可见]]。
- ## Strongly-Happens-before
	- [[Strongly-happens-before 关系]]略有不同，但在大多数情况下归结为相同。上述描述的两条规则适用：如果操作A [[synchronizes-with]] 操作B同步，或操作A [[sequenced-before]] 操作B，那么A [[strongly-happens-before]] B。
	  传递排序也适用：如果A strongly-happens-before B，且B strongly-happens-before C，那么A strongly-happens-before C。
	- 区别在于标记为[[memory_order_consume]]的操作参与[[inter-thread happens-before]]关系（因此是happens-before关系），但不参与[[strongly-happens-before]]关系。由于绝大多数代码不应该使用memory_order_consume，这种区别实际上可能影响不大。
- 这些是强制执行线程间操作顺序的关键规则。