alias:: factory method, 工厂方法模式

- 工厂方法模式（Factory Method Pattern）是[[创建型设计模式]]中的一种，它定义了一个创建对象的接口，但将实际的对象创建工作**推迟到子类**中完成。这样的设计可以增加程序的灵活性，通过引入工厂类的概念来避免客户端与具体产品类的直接依赖，从而降低系统的耦合度。
- ### 工厂方法模式的组成部分
	- **抽象产品（Abstract Product）**：定义了产品的接口，工厂方法所创建的对象都必须实现这个接口。
	- **具体产品（Concrete Product）**：抽象产品的实现类。
	- **抽象工厂（Abstract Factory）**：声明了工厂方法，该方法返回一个抽象产品。
	- **具体工厂（Concrete Factory）**：抽象工厂的子类，实现了工厂方法以创建具体产品的实例。
- ### 优点
	- **增强了系统的灵活性**：因为工厂方法模式实现了[[开闭原则]]。新增具体产品时，只需增加相应的具体工厂类，无需修改原有系统代码。
	  logseq.order-list-type:: number
	- **增加了代码的可维护性**：将具体产品的创建延迟到具体工厂中，减少了客户端与具体产品之间的依赖关系。
	  logseq.order-list-type:: number
- ### 示例：日志记录器
  
  假设我们需要一个日志记录系统，它可以记录信息到不同的地方（例如：控制台、文件）。使用工厂方法模式，我们可以定义一个日志记录器工厂接口和多个具体的日志记录器工厂类，每个工厂类负责创建特定类型的日志记录器。
- #### C++ 示例代码
  
  ```cpp
  #include <iostream>
  #include <memory>
  
  // 抽象产品：日志记录器
  class Logger {
  public:
    virtual ~Logger() {}
    virtual void Log(const std::string& message) = 0;
  };
  
  // 具体产品：控制台日志记录器
  class ConsoleLogger : public Logger {
  public:
    void Log(const std::string& message) override {
        std::cout << "Console Logger: " << message << std::endl;
    }
  };
  
  // 具体产品：文件日志记录器
  class FileLogger : public Logger {
  public:
    void Log(const std::string& message) override {
        // 假设这里将消息记录到文件
        std::cout << "File Logger: " << message << std::endl;
    }
  };
  
  // 抽象工厂：日志记录器工厂
  class LoggerFactory {
  public:
    virtual ~LoggerFactory() {}
    virtual std::unique_ptr<Logger> CreateLogger() = 0;
  };
  
  // 具体工厂：控制台日志记录器工厂
  class ConsoleLoggerFactory : public LoggerFactory {
  public:
    std::unique_ptr<Logger> CreateLogger() override {
        return std::make_unique<ConsoleLogger>();
    }
  };
  
  // 具体工厂：文件日志记录器工厂
  class FileLoggerFactory : public LoggerFactory {
  public:
    std::unique_ptr<Logger> CreateLogger() override {
        return std::make_unique<FileLogger>();
    }
  };
  
  // 客户端代码
  int main() {
    std::unique_ptr<LoggerFactory> loggerFactory = std::make_unique<ConsoleLoggerFactory>();
    auto logger = loggerFactory->CreateLogger();
    logger->Log("This is a console log.");
  
    loggerFactory = std::make_unique<FileLoggerFactory>();
    logger = loggerFactory->CreateLogger();
    logger->Log("This is a file log.");
  
    return 0;
  }
  ```
  
  在这个示例中，`LoggerFactory`是一个抽象工厂，它定义了一个`CreateLogger`方法。`ConsoleLoggerFactory`和`FileLoggerFactory`是具体的工厂类，它们实现了`CreateLogger`方法来创建对应类型的日志记录器对象。客户端代码通过工厂接口与日志记录器对象交互，而不需要知道具体的日志记录器类，从而实现了解耦和灵活性。
- ### 使用工厂模式的原因
	- 使用工厂模式（Factory Pattern），主要是为了解决对象创建过程中的复杂性和灵活性问题。工厂模式通过定义一个用于创建对象的接口，让子类决定实例化哪一个类，有助于系统在不直接指定对象的具体类型的情况下，生成对象。以下是使用工厂模式的几个主要原因：
	- 1. 解耦（Decoupling）：工厂模式可以减少应用程序中各个类之间的耦合。通过使用工厂类而非直接实例化类，可以在不影响客户端代码的情况下更换或添加新的类，从而提高系统的灵活性。
	- 2. **控制创建过程**：工厂模式使得创建过程集中管理，如果对象创建逻辑需要变更，只需修改工厂类，而无需触及使用该对象的类。这对于复杂对象的创建，特别是当对象的创建需要依赖于特定的条件或配置时，尤其有用。
	- 3. 扩展性（Extensibility）：当需要引入新的产品类到系统中时，工厂模式允许你轻松添加更多的产品类，而无需修改现有代码。这符合开闭原则（Open-Closed Principle）。
	- 4. **复用性**（Reusability）：通过使用工厂模式，可以更容易地复用已有的对象，特别是在涉及到**复杂对象创建和管理**的重复操作时。
	- 5. 接口隔离：工厂模式提供了一个创建对象的接口，隐藏了具体类的构造函数和初始化代码。这样，用户只需通过接口与工厂交互，而不需要知道具体类的实现细节，降低了系统的复杂性。
	- 6. **产品族和产品等级结构管理**：在更复杂的场景下，如[[抽象工厂模式]]，工厂模式能够管理相关的产品族，同时也能保持在不同产品族中对象的创建一致性。