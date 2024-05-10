alias:: 访问者模式, 访问器模式

- ^^访问者模式^^（Visitor Pattern）是一种[[行为型设计模式]]，用于将操作与对象结构分离。通过访问者模式，你可以**在不改变对象结构的情况下向其添加新的操作**，从而实现[[开闭原则]]。该模式适用于复杂对象结构，其中需要对不同类型的对象执行多种操作。
- ### 访问者模式的组成：
	- **访问者接口（Visitor Interface）**：
	  logseq.order-list-type:: number
		- 定义对对象结构中的每个类型的访问方法，例如 `visit(ElementType)`。
	- **具体访问者（Concrete Visitor）**：
	  logseq.order-list-type:: number
		- 实现访问者接口，定义对每种类型执行的操作。
	- **元素接口（Element Interface）**：
	  logseq.order-list-type:: number
		- 定义一个 `accept(Visitor)` 方法，允许访问者访问该元素。
	- **具体元素（Concrete Elements）**：
	  logseq.order-list-type:: number
		- 实现元素接口，并接受访问者。
- ### 访问者模式的关键特点：
	- **分离操作与对象结构**：访问者模式将^^操作^^与^^对象结构^^分离，允许在不改变对象结构的情况下添加新的操作。
	- **支持多种操作**：可以通过添加新的访问者来增加对对象结构的操作。
	- **增强可维护性**：访问者模式有助于避免在对象结构中添加新的操作时需要修改原有类。
- ### 示例代码：
  以下是使用 C++ 实现访问者模式的一个示例，展示了如何对不同类型的形状执行操作。
  ```cpp
  #include <iostream>
  #include <memory>
  
  // 访问者接口
  class Visitor {
  public:
    virtual ~Visitor() {}
    virtual void visit(class Circle& circle) = 0;
    virtual void visit(class Rectangle& rectangle) = 0;
  };
  
  // 元素接口
  class Shape {
  public:
    virtual ~Shape() {}
    virtual void accept(Visitor& visitor) = 0;
  };
  
  // 具体元素：圆
  class Circle : public Shape {
  public:
    void accept(Visitor& visitor) override {
        visitor.visit(*this);  // 让访问者访问自身
    }
  };
  
  // 具体元素：矩形
  class Rectangle : public Shape {
  public:
    void accept(Visitor& visitor) override {
        visitor.visit(*this);  // 让访问者访问自身
    }
  };
  
  // 具体访问者：绘制形状
  class DrawVisitor : public Visitor {
  public:
    void visit(Circle& circle) override {
        std::cout << "Drawing Circle." << std::endl;
    }
  
    void visit(Rectangle& rectangle) override {
        std::cout << "Drawing Rectangle." << std::endl;
    }
  };
  
  // 具体访问者：计算面积
  class AreaVisitor : public Visitor {
  public:
    void visit(Circle& circle) override {
        std::cout << "Calculating area of Circle." << std::endl;
    }
  
    void visit(Rectangle& rectangle) override {
        std::cout << "Calculating area of Rectangle." << std::endl;
    }
  };
  
  // 客户端代码
  int main() {
    std::vector<std::shared_ptr<Shape>> shapes;
    shapes.push_back(std::make_shared<Circle>());
    shapes.push_back(std::make_shared<Rectangle>());
  
    DrawVisitor drawVisitor;
    AreaVisitor areaVisitor;
  
    // 对所有形状执行绘制操作
    for (auto& shape : shapes) {
        shape->accept(drawVisitor);
    }
  
    // 对所有形状执行计算面积操作
    for (auto& shape : shapes) {
        shape->accept(areaVisitor);
    }
  
    return 0;
  }
  ```
  在这个示例中，`Shape` 是元素接口，`Circle` 和 `Rectangle` 是具体元素。`Visitor` 是访问者接口，`DrawVisitor` 和 `AreaVisitor` 是具体访问者，分别定义了对 `Circle` 和 `Rectangle` 执行的操作。通过 `accept` 方法，元素可以接受访问者，并调用相应的访问方法。
- ### 使用场景：
	- 当你需要在不改变对象结构的情况下添加新的操作时。
	- 当对象结构包含多种不同类型的对象，并需要对它们执行不同的操作时。
	- 当操作逻辑复杂，放在对象内部可能导致代码复杂度增加时。
- ### 注意事项：
	- **过度复杂**：如果对象结构简单，可能不需要访问者模式。
	- **违反开闭原则**：如果需要增加新的元素类型，可能需要修改所有访问者，这可能违反[[开闭原则]]。
- 访问者模式提供了一种灵活的方式来在不改变对象结构的情况下添加新的操作，使得对象结构与操作分离。它适用于复杂对象结构，其中可能需要对不同类型的对象执行多种操作。