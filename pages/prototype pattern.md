alias:: 原型模式

- 原型模式（Prototype Pattern）是一种[[创建型设计模式]]，它用于创建重复的对象，同时又能保证性能。这种模式的核心思想是通过**复制一个已存在的实例来返回新的实例**，而不是通过新的实例的标准方式（如使用 new 关键字）来创建。原型模式允许对象在不知道具体类型的情况下生成其自身的精确副本。
- ### 原型模式的组成：
	- **原型接口（Prototype Interface）**：
	  logseq.order-list-type:: number
		- 定义了用于复制现有对象以生成新对象的方法。
	- **具体原型（Concrete Prototype）**：
	  logseq.order-list-type:: number
		- 实现原型接口的类，定义用于创建当前对象副本的具体操作。
	- **客户（Client）**：
	  logseq.order-list-type:: number
		- 创建新对象的用户，使用原型接口复制现有对象。
- ### 原型模式的关键特点：
	- **简化创建过程**：通过复制一个原型避免了类的初始化过程。
	- **优化性能**：特别是当对象的**创建成本很高**时，**复制一个已经存在的实例使程序运行更高效**。
	- **动态增加或减少产品类**：原型模式允许通过注册和删除原型实现在运行时动态改变可用的产品类型。
- ### 示例代码：
  以下是使用 C++ 实现原型模式的示例，假设我们有一个用于处理图形对象的系统，其中每种类型的图形都可以通过复制现有实例来创建：
  
  ```cpp
  #include <iostream>
  #include <unordered_map>
  #include <string>
  #include <memory>
  
  // 原型接口
  class Shape {
  public:
    virtual ~Shape() {}
    virtual std::unique_ptr<Shape> clone() = 0;
    virtual void draw() = 0;
  };
  
  // 具体原型：Rectangle
  class Rectangle : public Shape {
  public:
    std::unique_ptr<Shape> clone() override {
        return std::make_unique<Rectangle>(*this);
    }
    void draw() override {
        std::cout << "Drawing Rectangle" << std::endl;
    }
  };
  
  // 具体原型：Circle
  class Circle : public Shape {
  public:
    std::unique_ptr<Shape> clone() override {
        return std::make_unique<Circle>(*this);
    }
    void draw() override {
        std::cout << "Drawing Circle" << std::endl;
    }
  };
  
  // 客户端代码
  class ShapeRegistry {
    std::unordered_map<std::string, std::unique_ptr<Shape>> shapes;
  public:
    ShapeRegistry() {
        shapes["Rectangle"] = std::make_unique<Rectangle>();
        shapes["Circle"] = std::make_unique<Circle>();
    }
  
    std::unique_ptr<Shape> createShape(const std::string& type) {
        return shapes[type]->clone();
    }
  };
  
  int main() {
    ShapeRegistry registry;
    auto shape1 = registry.createShape("Circle");
    auto shape2 = registry.createShape("Rectangle");
  
    shape1->draw();  // 输出: Drawing Circle
    shape2->draw();  // 输出: Drawing Rectangle
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当直接创建对象的成本很高时，而复制成本比较低。
	- 当需要隐藏客户代码和创建新实例的复杂逻辑时。
	- 当系统需要独立于其产品的创建、组合或表示时。
- 原型模式通过允许对象自我复制，简化了对象创建的复杂性，同时使代码更易于扩展，适用于需要大量相似对象的场合。