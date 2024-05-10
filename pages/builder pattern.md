alias:: 建造者模式, 构建者模式, 构建器模式

- 构建者模式（Builder Pattern）是一种[[创建型设计模式]]，用于处理具有多个组件的复杂对象的构造问题。这种模式允许客户端**逐步构建复杂对象**，而不必直接构造一个包含大量参数的复杂对象，这通常会使构造过程变得复杂和错误易发。通过使用指定的构建者对象来封装构造一个特定对象的所有复杂逻辑，构建者模式可以使代码更加清晰，易于理解和维护。
- ### 构建者模式的组成：
	- **产品（Product）**：
	  logseq.order-list-type:: number
		- 最终要构建的复杂对象。
	- **抽象构建者（Builder）**：
	  logseq.order-list-type:: number
		- 为创建一个 Product 对象的各个部分指定抽象接口。
	- **具体构建者（Concrete Builder）**：
	  logseq.order-list-type:: number
		- 实现 Builder 接口，提供构建过程的具体实现。它维护由它构建的产品，并提供一个接口用于检索构建的产品。
	- **指挥者（Director）**：
	  logseq.order-list-type:: number
		- 构造一个使用 Builder 接口的对象。
		- 指挥者知道如何**组织和协调每个部分的构建**，以便产生最终产品。
	- ((6623de9e-2f6e-4a59-9254-3f964d3855af))
- ### 构建者模式的关键特点：
	- **封装性**：用户不需要知道每个内部组件是如何构建的。
	- **构建和表示分离**：构建者隐藏了该产品是如何组装的，只需要知道它由哪些部分组成。
	- **控制构建的细节**：可以更精细地控制产品的构建过程。
- ### 示例代码：
  以下是使用 C++ 实现构建者模式的示例，构建不同类型的汽车：
  ```cpp
  #include <iostream>
  #include <string>
  #include <memory>
  
  // 产品：汽车
  class Car {
  public:
    void setEngine(const std::string& engine) {
        this->engine = engine;
    }
    void setSeats(int seats) {
        this->seats = seats;
    }
    void setInfo() {
        std::cout << "Car with " << engine << " engine and " << seats << " seats.\n";
    }
  private:
    std::string engine;
    int seats;
  };
  
  // 抽象构建者
  class CarBuilder {
  public:
    virtual ~CarBuilder() {}
    virtual void buildEngine() = 0;
    virtual void buildSeats() = 0;
    virtual std::unique_ptr<Car> getCar() = 0;
  };
  
  // 具体构建者
  class SedanBuilder : public CarBuilder {
    std::unique_ptr<Car> car;
  public:
    SedanBuilder() { this->car = std::make_unique<Car>(); }
    void buildEngine() override {
        this->car->setEngine("Sedan Engine");
    }
    void buildSeats() override {
        this->car->setSeats(5);
    }
    std::unique_ptr<Car> getCar() override {
        return std::move(this->car);
    }
  };
  
  // 指挥者
  class Director {
  public:
    void constructSportsCar(CarBuilder& builder) {
        builder.buildEngine();
        builder.buildSeats();
    }
  };
  
  int main() {
    SedanBuilder builder;
    Director director;
  
    director.constructSportsCar(builder);
    std::unique_ptr<Car> car = builder.getCar();
    car->setInfo();
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当创建复杂对象的算法应独立于对象的组成部分以及它们的装配方式时。
	- 当构造过程必须允许被构造的对象有不同的表示时。
- 构建者模式通过将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。这为构建复杂对象提供了灵活性和控制力。