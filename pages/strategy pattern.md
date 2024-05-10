alias:: 策略模式

- 策略模式（Strategy Pattern）是一种[[行为型模式]]，它允许**在运行时选择算法或行为的具体实现**。策略模式定义了一系列的算法，并将每一个算法封装起来，使它们可以互换使用，这使得算法可以独立于使用它的客户端变化。
- ### 策略模式的三个主要组成部分：
	- **策略接口（Strategy Interface）**：
	  logseq.order-list-type:: number
		- 这是一个公共接口，它定义了所有支持的算法的公共操作。每个算法都以不同的方式实现这个接口。
	- **具体策略类（Concrete Strategy Classes）**：
	  logseq.order-list-type:: number
		- 实现策略接口的类，每个类封装了一个具体的算法或行为。
	- **上下文（Context）**：
	  logseq.order-list-type:: number
		- 使用策略接口的类。上下文不直接执行算法，而是持有一个策略接口的引用，并通过这个引用调用具体策略实现的算法。
	- ((66227b60-b50a-4bba-82aa-2b15d5dbcfe7))
- ### 策略模式的关键特点：
	- **分离和封装**：策略模式将算法的定义与其使用分离开来，每个策略都被封装在不同的策略类中。
	- **替换和扩展**：策略模式允许在运行时替换算法，也便于添加新的算法，而不影响到使用算法的客户端代码。
	- **简化单元测试**：每个策略作为一个独立的类，可以单独测试。
- ### 示例代码：
  以下是 C++ 中实现策略模式的一个简单示例，假设我们有多种排序策略，并希望能够动态选择使用哪种排序算法。
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>
  
  // 策略接口
  class SortingStrategy {
  public:
    virtual ~SortingStrategy() {}
    virtual void sort(std::vector<int>& data) = 0;
  };
  
  // 具体策略类：冒泡排序
  class BubbleSort : public SortingStrategy {
  public:
    void sort(std::vector<int>& data) override {
        for (size_t i = 0; i < data.size() - 1; i++) {
            for (size_t j = 0; j < data.size() - i - 1; j++) {
                if (data[j] > data[j + 1]) {
                    std::swap(data[j], data[j + 1]);
                }
            }
        }
        std::cout << "Sorted using Bubble Sort.\n";
    }
  };
  
  // 具体策略类：快速排序
  class QuickSort : public SortingStrategy {
  public:
    void sort(std::vector<int>& data) override {
        std::sort(data.begin(), data.end()); // 使用标准库的排序实现快速排序
        std::cout << "Sorted using Quick Sort.\n";
    }
  };
  
  // 上下文
  class SortedData {
  private:
    std::vector<int> data;
    SortingStrategy* strategy;
  
  public:
    SortedData(const std::vector<int>& d) : data(d), strategy(nullptr) {}
  
    void setStrategy(SortingStrategy* s) {
        strategy = s;
    }
  
    void sort() {
        if (strategy) {
            strategy->sort(data);
        }
        for (int i : data) {
            std::cout << i << " ";
        }
        std::cout << std::endl;
    }
  };
  
  int main() {
    std::vector<int> data = {9, 7, 5, 3, 1};
    SortedData sortedData(data);
  
    BubbleSort bubble;
    QuickSort quick;
  
    sortedData.setStrategy(&bubble);
    sortedData.sort();
  
    sortedData.setStrategy(&quick);
    sortedData.sort();
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当你有多种类似的行为，或算法有许多变体时。
	- 当算法使用的客户端代码不应受到算法选择的影响时。
	- 当你的类中包含大量条件选择语
	  句，这些语句依赖于类的行为时，使用策略模式可以将这些条件的逻辑抽象出来。
- 策略模式通过提供一个灵活的方式来切换算法或行为，使得算法可以根据场景自由切换，从而增加代码的灵活性和可维护性。