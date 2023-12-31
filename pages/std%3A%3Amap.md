- ``` cpp
  namespace pmr {
  template<
      class Key,
      class T,
      class Compare = std::less<Key>
  > using map = std::map<Key, T, Compare,
                         std::pmr::polymorphic_allocator<std::pair<const Key, T>>>;
  }
  ```
- `std::map` 是一个[[有序关联容器]]，它包含具有唯一键的 *键-值对* 。这些键通过比较函数 `Compare` 进行排序。查找、删除和插入操作具有对数时间复杂度。通常情况下，`std::map` 被实现为[[红黑树]]。
- 在标准库使用比较要求的任何地方，*唯一性* 是通过 *等价关系* 来确定的。粗略地说，如果两个对象 a 和 b 互不小于对方（即 `!comp(a, b) && !comp(b, a)`），则它们被视为**等价**（不唯一）。
	- 也就是[[std::map]]每个`key`都是唯一的。进而一个`key`只能对应一个`value`。
	  [[std::multimap]]中可以存在多个相同的`key`，也可以存在多个完全一样的 键值对。
-