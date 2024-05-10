alias:: 抽象工厂模式

- 抽象工厂模式（Abstract Factory Pattern）是一种[[创建型设计模式]]，用于处理多个具有相同主题的工厂之间的接口。它提供了一种方式，可以在不指定具体类的情况下创建一系列相关或相互依赖的对象。抽象工厂模式的关键在于使用多个工厂方法，每个工厂方法负责创建不同种类的对象。
- ### 抽象工厂模式的组成部分
	- **抽象工厂（Abstract Factory）**：提供一个接口，用于创建相关或依赖对象的家族，而不需要明确指定具体类。
	- **具体工厂（Concrete Factory）**：实现抽象工厂的操作，生产具体的产品。
	- **抽象产品（Abstract Product）**：为一类产品对象声明一个接口。
	- **具体产品（Concrete Product）**：抽象产品的实现；被相应的具体工厂创建。
	- **客户端（Client）**：仅使用由抽象工厂和抽象产品定义的接口。
	- > ((6621440b-96d3-4d9a-b234-9f38b2f5e728))
- ### 优点
	- 1. **促进模块化**：客户端代码只需与抽象接口打交道，不需要与具体类直接交互。
	- 2. **易于更换产品系列**：通过使用具体的工厂类，可以轻松更换产品系列而不影响客户端代码。
	- 3. **增强程序的灵活性和可扩展性**：新增产品族或产品等级结构时，不需要修改已有系统，符合[[开闭原则]]。
- ### 示例：UI 组件库
  假设我们正在开发一个跨平台的UI库，需要根据不同的操作系统（如Windows、MacOS）创建不同风格的UI组件（如按钮、文本框）。
- #### C++ 实现
  
  ```cpp
  #include <iostream>
  #include <memory>
  
  // 抽象产品：按钮
  class Button {
  public:
    virtual void paint() = 0;
    virtual ~Button() {}
  };
  
  // 抽象产品：文本框
  class TextField {
  public:
    virtual void paint() = 0;
    virtual ~TextField() {}
  };
  
  // 抽象工厂：UI组件工厂
  class GUIFactory {
  public:
      virtual std::unique_ptr<Button> createButton() = 0;
      virtual std::unique_ptr<TextField> createTextField() = 0;
      virtual ~GUIFactory() {}
  };
  
  // 具体产品：Windows按钮
  class WindowsButton : public Button {
  public:
    void paint() override { std::cout << "Rendering a button in Windows style.\n"; }
  };
  
  // 具体产品：Windows文本框
  class WindowsTextField : public TextField {
  public:
    void paint() override { std::cout << "Rendering a text field in Windows style.\n"; }
  };
  
  // 具体工厂：Windows UI组件工厂
  class WindowsFactory : public GUIFactory {
  public:
    std::unique_ptr<Button> createButton() override {
        return std::make_unique<WindowsButton>();
    }
    std::unique_ptr<TextField> createTextField() override {
        return std::make_unique<WindowsTextField>();
    }
  };
  
  // 客户端代码
  int main() {
    std::unique_ptr<GUIFactory> factory = std::make_unique<WindowsFactory>();
    auto button = factory->createButton();
    auto textField = factory->createTextField();
    button->paint();
    textField->paint();
  
    // 对于MacOS或其他操作系统，可以创建相应的工厂和产品类
    // 并使用相同的方式来构建和使用UI组件
  
    return 0;
  }
  ```
  
  在这个例子中，`GUIFactory`是一个抽象工厂，它定义了创建UI组件的方法。`WindowsFactory`是具体的工厂类，实现了这些方法来创建Windows风格的UI组件。客户端代码通过`GUIFactory`接口与UI组件交互，而无需关心组件的具体实现，这样就可以轻松地更换UI组件的风格，而不需要修改客户端代码。
- 抽象工厂模式使得添加新的产品族（如为另一个操作系统添加一套UI组件）变得容易，只需增加新的具体工厂和一系列产品实现即可，而不需要修改现有代码。这样做不仅提高了代码的可维护性和扩展性，也使得产品系列的更换变得非常灵活。
- ## 总结
	- 固定好要生成的产品的基类的组合（基类之间一般有依赖关系），每一类型产品选择哪个子类是可以变更的。
	- ### 优点
		- 规范出一个不会变更生成流程，避免流程上的错误和重复流程。
		  logseq.order-list-type:: number
		- 子类可以根据需求随意变更。
		  logseq.order-list-type:: number