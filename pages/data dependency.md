alias:: 数据依赖

- ## 获取-释放排序和[[memory_order_consume]]的数据依赖
	- `memory_order_consume` 是获取-释放排序模型的一部分，但在前面的描述中它显然缺失了。
	  id:: 65e45fd4-f490-4d8a-81de-f657c67e0644
	  这是因为`memory_order_consume`是特殊的：它完全关于数据依赖，并且它将数据依赖的细微差别引入了在[[inter-thread happens-before]] 关系。它也特别在于C++17标准明确建议你不要使用它。因此，这里仅为了完整性而覆盖：你**不应该在代码中使用`memory_order_consume`！**
	- 数据依赖的概念相对直接：如果第二个操作操作的是第一个操作的结果，那么这两个操作之间存在^^数据依赖^^。处理数据依赖的有两个新的关系：[[dependency-ordered-before]]和[[carries-a-dependency-to]]。
		- 像sequenced-before一样，[[carries-a-dependency-to]] 严格适用于[[单个线程]]内，并模型化操作之间的数据依赖；如果操作A 的结果用作 操作B 的操作数，则A [[携带依赖到]] B。如果操作A的结果是诸如 `int` 之类的标量类型的值，那么如果A的结果存储在一个变量中，并且该变量随后用作操作B的操作数，那么这种关系仍然适用。这种操作也是传递的，所以如果A携带依赖到B，且B携带依赖到C，则A携带依赖到C。
		- 另一方面，[[dependency-ordered-before]]关系可以适用于**线程之间**。它通过使用带有[[memory_order_consume]]标记的[[原子加载操作]]引入。这是`memory_order_acquire`的一个特殊情况，它将同步数据限制为直接依赖；一个带有`memory_order_release`、`memory_order_acq_rel`或`memory_order_seq_cst`标记的存储操作（A）是dependency-ordered-before一个带有`memory_order_consume`标记的加载操作（B），如果consume读取了存储的值。这与如果加载使用`memory_order_acquire`得到的synchronizes-with关系相反。如果这个操作（B）随后[[携带依赖到]]一些操作（C），那么A也是dependency-ordered-before C。
		- 如果这不影响[[inter-thread happens-before]]关系，那么它对同步目的没有任何好处，但它确实有影响：如果A是 dependency-ordered-before B，那么A也是 inter-thread happens-before B。
	- 这种内存排序的一个重要用途是，原子操作加载指向某些数据的指针。通过在加载上使用`memory_order_consume`并在之前的存储上使用`memory_order_release`，你确保了指向的数据被正确同步，而不对任何其他非依赖数据施加任何同步要求。
	- ## 示例
		- 下面的清单展示了这种场景的一个示例。
		  ``` cpp
		  /** 使用 std::memroy_order_consume 同步数据 */
		  struct X
		  {
		      int i;
		      std::string s;
		  };
		  std::atomic<X*> p;
		  std::atomic<int> a;
		  void create_x()
		  {
		      X* x=new X;
		      x->i=42;
		      x->s="hello";
		      a.store(99,std::memory_order_relaxed); // 1
		      p.store(x,std::memory_order_release); // 2
		  }
		  void use_x()
		  {
		      X* x;
		      while(!(x=p.load(std::memory_order_consume))) // 3
		      	std::this_thread::sleep(std::chrono::microseconds(1));
		      assert(x->i==42); // 4
		      assert(x->s=="hello"); // 5
		      assert(a.load(std::memory_order_relaxed)==99); // 6
		  }
		  int main()
		  {
		      std::thread t1(create_x);
		      std::thread t2(use_x);
		      t1.join();
		      t2.join();
		  }
		  ```
		- 尽管对B的存储先于对 p 的存储，且对 p 的存储被标记为`memory_order_release`，但对p的加载被标记为`memory_order_consume`。这意味着对p的存储仅发生在那些依赖于从p加载的值的表达式之前。这意味着对X结构体的数据成员的断言**保证不会触发**，因为从p的加载通过变量x carries a dependency to 这些表达式。另一方面，对a值的断言可能会也可能不会触发；这个操作不依赖于从p加载的值，因此对读取的值没有保证。这一点尤其明显，因为它被标记为`memory_order_relaxed`，正如你将看到的。
	- 有时，你不想要携带依赖的开销。你希望编译器能够在寄存器中缓存值并重新排序操作以优化代码，而不是纠结于依赖性。在这些场景中，你可以使用`std::kill_dependency()`来显式打破依赖链。[[std::kill_dependency()]]是一个简单的函数模板，它将提供的参数复制到返回值，但在此过程中打断了依赖链。例如，如果你有一个全局只读数组，并且在从另一个线程检索该数组的索引时使用`std::memory_order_consume`，你可以使用`std::kill_dependency()`来让编译器知道它不需要重新读取数组条目的内容，如下例所示：
	- ```cpp
	  int global_data[] = { … };
	  std::atomic<int> index;
	  void f() {
	    int i = index.load(std::memory_order_consume);
	    do_something_with(global_data[std::kill_dependency(i)]);
	  }
	  ```
	- 在真实代码中，你应该总是在可能会被诱惑使用`memory_order_consume`的地方使用`memory_order_acquire`，并且`std::kill_dependency`是不必要的。