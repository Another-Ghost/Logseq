- ``` cpp
  template< class T > class shared_ptr;
  ```
- `std::shared_ptr` 是一个[[智能指针]]，通过指针实现对象的 *共享拥有权*。多个 `shared_ptr` 对象可以拥有同一个对象。对象在以下情况下会被销毁并其内存被释放：
	- 拥有对象的最后一个 `shared_ptr` 被销毁。
	- 拥有对象的最后一个 `shared_ptr` 被分配另一个指针（通过[[operator =]]或 `reset()`）。
- 对象的销毁可以使用[[delete]]表达式或在 `shared_ptr` 创建时提供的自定义[[deleter]]。
- `shared_ptr` 可以共享对象的拥有权，同时存储另一个对象的指针。
  这个特性可以用于指向成员对象，同时拥有它们所属的对象。存储的指针可以通过 `get()`、[[解引用]]和 *比较操作符* 来访问。当[[use count]]达到零时，托管的指针 将传递给[[deleter]]。
- `shared_ptr` 也可以不拥有任何对象，这时称为 *empty*（即使空的 `shared_ptr` 可能有一个非空的存储指针，如果使用了[[aliasing constructor]]来创建它）。
- `shared_ptr` 的所有特化满足[[CopyConstructible]]、[[CopyAssignable]]和[[LessThanComparable]]的要求，并在上下文中可转换为 bool 类型。
- ## Multi-thread
  id:: 6541eb27-d1a2-4366-9088-c5a410762c37
  所有 成员函数（包括 复制构造函数 和 复制赋值函数 ）可以在不需要额外[[同步]]的情况下由多个[[线程]]调用，即使这些 实例 是 副本 并 共享 相同对象 的拥有权 。
  如果多个 执行线程 在没有 同步 的情况下访问相同的 `shared_ptr` 实例，而这些访问中的任何一个使用了 `shared_ptr` 的 非const成员函数，那么会发生[[数据竞争]]；可以使用 `shared_ptr` 的[原子函数重载]([[std::atomic_...<std::shared_ptr>]])来防止数据竞争 。
- # Notes
	- 对象的所有权只能通过将其值[[复制构造]]或[[复制赋值]]来共享给另一个 `shared_ptr`。使用另一个 `shared_ptr` 拥有的 原始底层指针 来构造新的 `shared_ptr` 会导致 *未定义行为* 。
	  logseq.order-list-type:: number
	- 但是，使用原始指针的构造函数（`template<class Y> shared_ptr(Y*)`）和 `template<class Y> void reset(Y*)` 成员函数只能使用 完整类型的指针 调用。
	  logseq.order-list-type:: number
	  id:: 65421f2d-ad40-4ec8-920f-8adcaf43c958
	  #+BEGIN_CAUTION
	       [[std::unique_ptr]]可以从指向不完整类型的原始指针构造
	  #+END_CAUTION
	- logseq.order-list-type:: number
	  `std::shared_ptr<T>` 中的 `T` 可以是函数类型：在这种情况下，它管理一个指向函数的指针，而不是对象指针。这有时用于在引用其任何函数的情况下保持[[动态库]]或[[插件]]加载：
	  ```cpp
	  void del(void(*)()) {}
	  
	  void fun() {}
	  
	  int main()
	  {
	      std::shared_ptr<void()> ee(fun, del);
	      (*ee)();
	  }
	  ```
- ## 实现注释
  id:: 65422260-e6f3-4b1e-81a6-663a9b5f6779
	- 在典型的实现中，`shared_ptr` 仅保存两个指针：
		- 存储的指针（由 `get()` 返回的指针）。
		  logseq.order-list-type:: number
		- [[control block]]的指针。
		  logseq.order-list-type:: number
	- 控制块是一个 *动态分配* 的对象，其中包含：
		- 管理的对象的指针 或 管理的对象本身。
		- [[deleter]]（[[type-erased]]）。
		- [[allocator]]（[[type-erased]]）。
		- 拥有 管理的对象 的 `shared_ptr` 数。
		- 引用 管理的对象 的[[weak_ptr]]数。
	- 当通过调用 `std::make_shared` 或 `std::allocate_shared` 创建 `shared_ptr` 时，[[control block]]和管理的对象的内存都是通过单次分配创建的。管理的对象在[[control block]]的数据成员中[[就地构造]]。当通过 `shared_ptr` 构造函数之一创建 `shared_ptr` 时，必须**分别为 管理的对象 和 控制块 分配内存。在这种情况下，control block 存储管理的对象的指针。
	  
	  `shared_ptr` 直接持有的指针是由 `get()` 返回的指针，而控制块持有的 指针/对象 是在 [[sharadowner]]数 达到零时 将被删除的 指针/对象 。这些指针**不一定相等**。
	  
	  `shared_ptr` 的 *析构函数* 会[[递减]][[控制块]]的 [[shared owner]]数。如果该计数达到零，控制块调用托管对象的析构函数。直到 `std::weak_ptr` 计数也达到零，控制块不会被释放。
	  
	  在现有的实现中，如果有一个共享指向同一个控制块的 `shared_ptr`，则增加弱指针的计数（[1]，[2]）。
	  
	  为满足线程安全性要求，引用计数通常使用 `std::atomic::fetch_add` 的等效方法进行递增，使用 `std::memory_order_relaxed`（递减需要更强的排序来安全地销毁控制块）。
-