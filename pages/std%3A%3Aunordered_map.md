- ```cpp 
  namespace pmr {
      template <
          class Key,
          class T,
          class Hash = std::hash<Key>,
          class KeyEqual = std::equal_to<Key>
      >
      using unordered_map =
          std::unordered_map<Key, T, Hash, KeyEqual,
              std::pmr::polymorphic_allocator<std::pair<const Key, T>>>;
  }
  ```
- [[std::unordered_map]]是一个[[关联容器]]，包含具有*唯一键**的 *键-值对* 。对元素的查找、插入和删除具有平均 *常数时间复杂度* 。
- 在其内部，元素不按特定顺序排序，而是组织成[[bucket]]。元素被放入哪个桶完全**取决于**其[[键]]的[[哈希值]]。具有相同[[hash code]]的键出现在同一个[[桶]]中。这允许快速访问单个元素，因为一旦计算出哈希值，它就指向元素所在的确切桶。
- 如果在 map 的 key equality predicate 传递两个 *键* 时返回 true，则认为这两个键是 *等效的* 。
  如果两个键等效，[[哈希函数]]必须为这两个键返回相同的值。
-
- C++ STL 标准库中，不仅是 unordered_map 容器，所有无序容器的底层实现都采用的是[[哈希表]]存储结构。更准确地说，是用[[链地址法]]解决 数据存储位置 发生 *冲突* 的哈希表
  id:: 653e7107-974c-40df-8ee3-4d4b4e8e6e4b
-