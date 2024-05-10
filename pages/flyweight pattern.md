alias:: 享元模式

- 享元模式（Flyweight Pattern）是一种[[结构型设计模式]]，旨在通过**共享相同状态的对象**来**减少内存消耗**。这种模式适用于创建大量相似对象的场景，通过共享相同的内部状态，享元模式可以显著减少内存占用并提高性能。
- ### 享元模式的组成：
	- **享元接口（Flyweight Interface）**：
	  logseq.order-list-type:: number
		- 定义可以共享的对象的接口，这些对象有可共享的^^内部状态^^。
	- **具体享元类（Concrete Flyweight Class）**：
	  logseq.order-list-type:: number
		- 实现享元接口的类，维护内部状态，并提供用于显示外部状态的操作。
	- **非享元类（Non-Flyweight Class）**：
	  logseq.order-list-type:: number
		- 包含不适合共享的^^外部状态^^，如与对象实例关联的特定信息。
	- **享元工厂（Flyweight Factory）**：
	  logseq.order-list-type:: number
		- 管理和提供享元对象的工厂。它负责确保相同内部状态的对象被共享，而不是重新创建。
- ### 享元模式的关键特点：
	- **内存优化**：通过共享相同的内部状态，显著减少内存消耗。
	- **高性能**：避免创建大量相似的对象，提高内存和性能的效率。
	- **拆分状态**：将状态分为内部状态和外部状态，内部状态可以共享，外部状态由客户端提供。
- ### 示例代码：
  以下是 C++ 中实现享元模式的一个简单示例，展示了如何在多棵树的场景中共享树的特性：
  ```cpp
  #include <iostream>
  #include <unordered_map>
  #include <memory>
  #include <string>
  
  // 享元接口
  class TreeType {
  public:
    virtual ~TreeType() {}
    virtual void display(int x, int y) = 0; // 显示树的外部状态
  };
  
  // 具体享元类
  class ConcreteTreeType : public TreeType {
  private:
    std::string type; // 内部状态
    std::string color;
  
  public:
    ConcreteTreeType(const std::string& t, const std::string& c)
        : type(t), color(c) {}
  
    void display(int x, int y) override { // 外部状态由客户端提供
        std::cout << "Displaying " << type << " tree at (" << x << ", " << y
                  << ") with color " << color << std::endl;
    }
  };
  
  // 享元工厂
  class TreeTypeFactory {
  private:
    std::unordered_map<std::string, std::shared_ptr<TreeType>> treeTypes;
  
  public:
    std::shared_ptr<TreeType> getTreeType(const std::string& type, const std::string& color) {
        std::string key = type + "_" + color;
        auto it = treeTypes.find(key);
        if (it == treeTypes.end()) { // 如果不存在，则创建并添加
            treeTypes[key] = std::make_shared<ConcreteTreeType>(type, color);
        }
        return treeTypes[key];
    }
  };
  
  // 客户端代码
  int main() {
    TreeTypeFactory factory;
  
    // 获取共享的树类型
    auto oak = factory.getTreeType("Oak", "Green");
    auto pine = factory.getTreeType("Pine", "Dark Green");
  
    // 创建带有外部状态的树
    oak->display(10, 20);
    pine->display(30, 40);
    oak->display(50, 60);
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当需要创建大量相似对象，但这些对象的内部状态可以共享时。
	- 当对象的内存占用量较大，但可以通过共享来减少内存消耗时。
- ### 注意事项：
	- **状态拆分**：确保可以区分对象的内部状态和外部状态，内部状态可以共享，外部状态由客户端提供。
	- **对象管理**：享元工厂需要确保对享元对象的有效管理，避免对象泄漏或过度共享导致的问题。
	  
	  享元模式通过共享内部状态显著减少内存消耗，特别适用于需要大量相似对象的场景，如图形系统中的大量对象共享相同的外观。
	  <!--Converted by ToLogseq-->