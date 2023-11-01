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
	- 对象的所有权只能通过将其值[[复制构造]]或 copy assigning 给另一个 `shared_ptr` 来共享给另一个 `shared_ptr`。使用另一个 `shared_ptr` 拥有的原始底层指针来构造新的 `shared_ptr` 会导致 *未定义行为* 。
	  id:: 65421d71-5cf4-4612-9ae2-423abe7043d6
-