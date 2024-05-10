alias:: 迭代器模式

- 迭代器模式（Iterator Pattern）是一种行为型设计模式，用于在不暴露集合内部结构的情况下遍历集合中的元素。迭代器模式提供了一种统一的方式来访问集合中的元素，使得客户端可以在不同类型的集合上进行一致的遍历操作。
- ### 迭代器模式的组成：
	- **迭代器接口（Iterator Interface）**：
	  logseq.order-list-type:: number
		- 定义了遍历集合的接口，包括方法如 `first()`、`next()`、`isDone()`、`currentItem()` 等。
	- **具体迭代器（Concrete Iterator）**：
	  logseq.order-list-type:: number
		- 实现迭代器接口，用于遍历特定的集合。
	- **集合接口（Aggregate Interface）**：
	  logseq.order-list-type:: number
		- 定义了创建迭代器的接口。
	- **具体集合（Concrete Aggregate）**：
	  logseq.order-list-type:: number
		- 实现集合接口，创建具体的迭代器实例。
- ### 迭代器模式的关键特点：
	- **封装性**：迭代器可以遍历集合中的元素，而不需要暴露集合的内部结构。
	- **统一接口**：迭代器提供了统一的接口，使得客户端可以使用相同的方式遍历不同类型的集合。
	- **灵活性**：迭代器模式允许在不改变集合的情况下添加新的遍历方式。
- ### 示例代码：
  以下是使用 C++ 实现迭代器模式的一个示例，展示了如何使用迭代器遍历集合中的元素。
  ```cpp
  #include <iostream>
  #include <vector>
  #include <memory>
  
  // 迭代器接口
  class Iterator {
  public:
    virtual ~Iterator() {}
    virtual void first() = 0;
    virtual void next() = 0;
    virtual bool isDone() const = 0;
    virtual int currentItem() const = 0;
  };
  
  // 具体迭代器
  class VectorIterator : public Iterator {
  private:
    const std::vector<int>& data;
    size_t currentIndex;
  
  public:
    VectorIterator(const std::vector<int>& v) : data(v), currentIndex(0) {}
  
    void first() override {
        currentIndex = 0;
    }
  
    void next() override {
        if (currentIndex < data.size()) {
            currentIndex++;
        }
    }
  
    bool isDone() const override {
        return currentIndex >= data.size();
    }
  
    int currentItem() const override {
        if (!isDone()) {
            return data[currentIndex];
        }
        throw std::out_of_range("Iterator out of range");
    }
  };
  
  // 集合接口
  class Aggregate {
  public:
    virtual ~Aggregate() {}
    virtual std::unique_ptr<Iterator> createIterator() = 0;
  };
  
  // 具体集合
  class IntVector : public Aggregate {
  private:
    std::vector<int> data;
  
  public:
    void add(int value) {
        data.push_back(value);
    }
  
    std::unique_ptr<Iterator> createIterator() override {
        return std::make_unique<VectorIterator>(data);
    }
  };
  
  // 客户端代码
  int main() {
    IntVector intVector;
    intVector.add(1);
    intVector.add(2);
    intVector.add(3);
  
    auto iterator = intVector.createIterator();
  
    for (iterator->first(); !iterator->isDone(); iterator->next()) {
        std::cout << "Item: " << iterator->currentItem() << std::endl;
    }
  
    return 0;
  }
  ```
  
  在这个示例中，`Iterator` 是迭代器接口，`VectorIterator` 是具体迭代器，用于遍历 `std::vector<int>`。`Aggregate` 是集合接口，`IntVector` 是具体集合，提供了 `createIterator()` 方法来创建迭代器。客户端可以使用 `Iterator` 接口遍历集合，而不必了解集合的内部结构。
- ### 使用场景：
	- 当需要在不暴露集合内部结构的情况下遍历集合中的元素时。
	- 当需要提供多种遍历方式时。
	- 当集合的数据结构可能会变化，但遍历方式应保持一致时。
- ### 注意事项：
	- **过度复杂**：如果集合的结构简单，可能不需要迭代器模式。
	- **性能影响**：在某些情况下，迭代器的额外开销可能会影响性能。
- 迭代器模式提供了一种统一的方式来遍历集合，增强了集合操作的灵活性和封装性。