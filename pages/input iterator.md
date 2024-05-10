alias:: 输入迭代器

- 在 C++ 中，输入迭代器（Input Iterator）是一种迭代器，设计用于从序列中读取数据。输入迭代器的核心功能是能够访问序列中的数据，并且逐步向前移动，但它们通常不支持写入操作或向后移动。理解输入迭代器的底层原理可以帮助你更好地使用它们，并在需要时自定义迭代器行为。
- ### 基本特征和能力
- 输入迭代器提供的操作包括：
	- **解引用（Dereferencing）**：通过解引用操作（`*iterator`），可以访问迭代器当前指向的元素。
	  logseq.order-list-type:: number
	- **递增（Incrementing）**：通过递增操作（`++iterator` 和 `iterator++`），迭代器可以移动到序列中的下一个元素。
	  logseq.order-list-type:: number
	- **相等和不等比较**：输入迭代器支持比较操作（`==` 和 `!=`），用于检查两个迭代器是否相等或不等，这通常用于判断迭代器是否已经到达序列的结束。
	  logseq.order-list-type:: number
- ### 底层实现
- 虽然标准库提供了多种内置迭代器类型，但理解一个自定义输入迭代器的实现可以帮助我们深入理解其工作原理：
  ```cpp
  template<typename T>
  class InputIterator {
  public:
    using iterator_category = std::input_iterator_tag;
    using value_type = T;
    using difference_type = std::ptrdiff_t;
    using pointer = T*;
    using reference = T&;
  
    // 构造函数
    InputIterator(pointer ptr) : m_ptr(ptr) {}
  
    // 解引用操作符
    reference operator*() const { return *m_ptr; }
  
    // 前缀递增
    InputIterator& operator++() {
        m_ptr++;
        return *this;
    }
  
    // 后缀递增
    InputIterator operator++(int) {
        InputIterator tmp = *this;
        ++(*this);
        return tmp;
    }
  
    // 相等比较
    bool operator==(const InputIterator& other) const {
        return m_ptr == other.m_ptr;
    }
  
    // 不等比较
    bool operator!=(const InputIterator& other) const {
        return m_ptr != other.m_ptr;
    }
  
  private:
    pointer m_ptr;
  };
  ```
- 在这个示例中，`InputIterator` 是一个简单的输入迭代器，它封装了一个指向数据的指针。迭代器通过指针进行操作，允许遍历基础数据结构（如数组）。
- ### 使用情景
- 输入迭代器非常适用于那些只需要单向和一次性遍历的数据结构。例如，从文件流或网络流中读取数据时，你可能只能顺序地访问数据，而不可能回到之前的位置。
- ### 注意事项
	- 输入迭代器的设计不支持数据写入，如果需要写入能力，应考虑使用输出迭代器（Output Iterator）或更高级别的迭代器类型，如前向迭代器（Forward Iterator）。
	- 输入迭代器仅保证可以进行一次正向遍历。一旦通过迭代器访问了数据，再次访问相同的数据可能需要重新获取迭代器。
- 输入迭代器的简单和限制性设计使其成为处理顺序数据流的理想选择，尤其是在只需要读取而不需要修改数据的情况下。通过了解其底层实现，开发者可以更好地设计和使用符合特定需求的迭代器。
  <!--Converted by ToLogseq-->