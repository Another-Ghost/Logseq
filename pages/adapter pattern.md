alias:: 适配器模式

- 适配器模式（Adapter Pattern）是一种[[结构型设计模式]]，它允许不兼容的接口之间进行协作。通过**引入适配器对象，适配器模式将一个接口转换为另一个接口，从而使不兼容的类可以一起工作**。适配器模式在需要整合不同系统或接口的情况下非常有用。
- ### 适配器模式的组成：
	- **目标接口（Target Interface）**：
	  logseq.order-list-type:: number
		- 定义客户端需要的接口。
	- **适配器（Adapter）**：
	  logseq.order-list-type:: number
		- 实现目标接口，并持有与之不兼容的接口的引用。
		- 适配器通过转换调用，提供兼容的接口。
	- **不兼容接口（Adaptee）**：
	  logseq.order-list-type:: number
		- 需要适配的接口。通常是已经存在的类或系统。
	- **客户端（Client）**：
	  logseq.order-list-type:: number
		- 使用目标接口与适配器交互，而不需要知道适配器如何转换调用。
- ### 适配器模式的关键特点：
	- **接口转换**：适配器将一个接口转换为另一个接口，使得不兼容的类可以一起工作。
	- **提高兼容性**：适配器模式可以在不修改原始代码的情况下整合不同的系统或类。
	- **松耦合**：适配器使得客户端与不兼容的类之间的耦合关系变得松散。
- ### 示例代码：
  
  以下是使用 C++ 实现适配器模式的一个示例，展示了如何将旧接口转换为新接口，以确保客户端可以使用新的接口。
  
  ```cpp
  #include <iostream>
  #include <string>
  
  // 目标接口
  class Target {
  public:
    virtual ~Target() {}
    virtual void request() const {
        std::cout << "Target: Default request.\n";
    }
  };
  
  // 不兼容接口
  class Adaptee {
  public:
    void specificRequest() const {
        std::cout << "Adaptee: Specific request.\n";
    }
  };
  
  // 适配器
  class Adapter : public Target {
  private:
    Adaptee adaptee;
  
  public:
    void request() const override {
        adaptee.specificRequest();  // 转换调用
    }
  };
  
  // 客户端
  int main() {
    Target* target = new Target();
    target->request();  // 输出: Target: Default request.
  
    Adapter* adapter = new Adapter();
    adapter->request();  // 输出: Adaptee: Specific request.
  
    delete target;
    delete adapter;
  
    return 0;
  }
  ```
  
  在这个示例中，`Target` 是客户端期望的接口，`Adaptee` 是不兼容的旧接口，`Adapter` 是适配器，将 `Adaptee` 的接口转换为 `Target` 的接口。通过使用适配器，客户端可以使用 `Target` 接口与 `Adaptee` 交互，而无需修改 `Adaptee` 本身。
- ### 使用场景：
	- 当你需要将不兼容的接口整合在一起时。
	- 当你需要使用现有类的功能，但它们的接口与现有系统不兼容时。
	- 当你需要在不修改原始类的情况下引入新的接口时。
- ### 注意事项：
	- **过度使用**：不应过度使用适配器模式，否则可能导致系统变得复杂和难以维护。
	- **性能影响**：适配器模式可能引入额外的调用转换，可能影响性能。
- 适配器模式提供了一种将不兼容的接口整合在一起的方法，使得不同类和系统可以协同工作，从而提高代码的兼容性和灵活性。