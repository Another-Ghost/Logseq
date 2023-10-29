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
- 在其内部，元素不按特定顺序排序，而是组织成[[bucket]]。元素被放入哪个桶完全取决于其[[键]]的[[哈希值]]。具有相同[[hash code]]的键出现在同一个[[桶]]中。这允许快速访问单个元素，因为一旦计算出哈希值，它就指向元素所在的确切桶。
- 如果两个键在映射的键相等谓词传递这两个键时返回 true，则认为这两个键是等效的。如果两个键等效，哈希函数必须为这两个键返回相同的值。