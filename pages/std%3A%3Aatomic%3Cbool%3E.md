- 最基本的原子整型类型就是 `std::atomic<bool>` ，它有着比 `std::atomic_flag` 更加齐全的布尔标志特性。虽然不能拷贝构造和拷贝赋值，但可以使用非原子的 `bool` 类型进行构造，所以可以初始化为 `true` 或 `false` ，并且可以从非原子 `bool` 变量赋值给 `std::atomic<bool> `：
  ``` cpp
  std::atomic<bool> b(true);
  b=false;
  ``` 
  另外，非原子 `bool` 类型的赋值操作不同于通常的操作(转换成对应类型的引用，再赋给对应的对象)：它返回一个 `bool` 值来代替指定对象。原子类型中的另一种模式：通过返回值(返回相关的非原子类型)完成赋值。如果原子变量的引用返回了，任何依赖于这个赋值结果的代码都需要显式加载。问题是，结果可能会被其他线程修改。通过返回非原子值进行赋值的方式，可以避免多余的加载过程，并得到实际存储的值。
- 同样，`test_and_set()` 也可以替换为更加通用的 `exchange()`，`exchange()`允许使用新选的值替换已存储的值，并且会自动检索原始值。 `std::atomic<bool>` 也支持对值的(不修改)查找，其会将对象隐式的转换为普通的`bool`值，或显示的调用 `load()` 来完成。`store()` 是一个存储操作，而 `load()` 是一个加载操作，`exchange()` 是一个“读-改-写” 操作：
  ``` cpp
  std::atomic<bool> b;
  bool x=b.load(std::memory_order_acquire);
  b.store(true);
  x=b.exchange(false, std::memory_order_acq_rel);
  ```
- ## 存储一个新值与否取决于当前值
	- 这种新型操作叫做[[比较交换]]，它的形式表现为 `compare_exchange_weak()` 和
	  `compare_exchange_strong()` 。
	  “比较/交换”操作是[[原子类型编程]]的基石，它比较原子变量的当前值和期望值，当两值相等时，存储所提供值。当两值不等，期望值就会被更新为[[原子变量]]中的值。“比较/交换”函数值是一个 `bool` 变量，当返回 `true` 时执行存储操作。当存储完成(因为只相等)，则操作是成功的，否则即为失败。操作成功是返回`true` ，失败时返回 `false` 。
	  对于 `compare_exchange_weak()` ，当原始值与预期值一致时，存储也可能会不成功。在这种情况中变量的值不会发生改变，并且 `compare_exchange_weak()` 的返回值是 `false` 。这最可能发生在缺少单条CAS操作(“比较-交换”指令)的机器上，当处理器不能保证这个操作能够原子的完成——可能因为线程的操作执行到必要操作的中间时被切换，并且另一个线程将会被操作系统调度(这里线程数多于处理器数量)，称为“伪失败”(spurious failure)，因为造成这种情况的是时间，而不是变量值。
	  因为 compare_exchange_weak() 可以伪失败，所以通常会配合一个循环使用：
	- 这个新的操作被称为[[比较-交换]]，它以 `compare_exchange_weak()`和 `compare_exchange_strong()`成员函数的形式出现。比较-交换操作是使用[[原子类型]]编程的基石；它将原子变量的值与提供的预期值进行比较，并在它们相等时存储提供的期望值。如果值不相等，预期值将更新为原子变量的值。
	- 比较-交换函数的返回类型是 `bool`，如果执行了存储则为 `true` ，否则为 `false` 。如果存储完成（因为值相等），则操作被认为是成功的，否则失败；返回值为 `true` 表示成功，为 `false` 表示失败。
	- 对于 `compare_exchange_weak()` ，即使原始值等于预期值，存储也可能不成功，在这种情况下，变量的值不变，`compare_exchange_weak()` 的返回值为 `false` 。这种情况最有可能发生在缺乏[[比较-交换指令]]的机器上，如果处理器不能保证操作已经原子性地完成——可能是因为执行操作的线程在必要的指令序列中间被切换出去，而另一个线程被操作系统调度到它的位置。这被称为[[假性失败]]，因为失败的原因是时间函数，而不是变量的值。
	- 因为 `compare_exchange_weak()` 可能会偶尔失败，所以通常需要在循环中使用它：
	  ``` cpp
	  bool expected=false; 
	  extern atomic b; // 在其他地方设置 
	  while(!b.compare_exchange_weak(expected,true) && !expected);
	  ```
	  在这种情况下，只要 `expected` 仍然为 `false` ，就会继续循环，这表明 `compare_exchange_weak()` 调用失败是偶然的。
	- 另一方面，`compare_exchange_strong()`保证只有在值不等于预期值时才返回 `false`。这可以消除像所示的那种循环的需要，像是你想知道是否成功地改变了一个变量，或者是其他线程先到达那里。
	- 如果你想改变变量的初始值（可能是依赖于当前值的更新值），预期值的更新变得有用；每次循环，预期值都会被重新加载，所以如果在此期间没有其他线程修改值，那么下一次循环时 `compare_exchange_weak()` 或 `compare_exchange_strong()` 的调用应该会成功。如果要存储的值的计算很简单，那么使用`compare_exchange_weak()`可能会有益，以避免在`compare_exchange_weak()`可能会偶然失败的平台上出现双重循环（因此`compare_exchange_strong()`包含一个循环）。另一方面，如果要存储的值的计算耗时，那么使用`compare_exchange_strong()`可能更有意义，以避免在预期值未改变时重新计算要存储的值。对于`std::atomic<bool>`，这并不那么重要——毕竟只有两种可能的值——但对于更大的原子类型，这可能会有所不同。
	  id:: 65dd9266-d66a-4435-9d52-8848d4142bd7
	- 比较-交换函数也很特殊，因为它们可以接受两个内存排序参数。这允许在成功和失败的情况下内存排序语义有所不同；成功的调用可能希望有内存_order_acq_rel语义，而失败的调用则有内存_order_relaxed语义。失败的比较-交换不会进行存储，所以它不能有内存_order_release或内存_order_acq_rel语义。因此，不允许将这些值作为失败的排序提供。你也不能为失败提供比成功更严格的内存排序；如果你希望失败时有内存_order_acquire或内存_order_seq_cst语义，你也必须为成功指定这些语义。
	- 如果你没有为失败指定一个排序，那么默认认为它与成功的排序相同，只是去掉了排序的释放部分：memory_order_release变为memory_order_relaxed，memory_order_acq_rel变为memory_order_acquire。如果你既没有指定成功，也没有指定失败，它们默认为memory_order_seq_cst，如常规一样，为成功和失败提供完全的顺序排序。以下两个对compare_exchange_weak()的调用是等价的：