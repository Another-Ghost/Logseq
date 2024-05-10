alias:: 职责链模式, 责任链模式
id:: 66255b18-4d86-4261-b5de-c31b886ee373

- ^^责任链模式^^（Chain of Responsibility Pattern）是一种[[行为型设计模式]]，允许多个处理程序在一条链上处理请求。**每个处理程序都包含一个指向下一个处理程序的引用，请求在链上依次传递，直到找到可以处理请求的处理程序或到达链的末端**。责任链模式有助于避免请求处理的硬编码，并提高系统的灵活性和可扩展性。
- ### 责任链模式的组成：
	- **处理程序接口（Handler Interface）**：
	  logseq.order-list-type:: number
		- 定义处理请求的接口，包括处理请求的方法和设置下一个处理程序的方法。
	- **具体处理程序（Concrete Handler）**：
	  logseq.order-list-type:: number
		- 实现处理程序接口，负责处理请求。
		- 如果不能处理请求，它会将请求传递给下一个处理程序。
		  id:: 662609c1-faf1-49fa-a525-0179469b4992
	- **客户端（Client）**：
	  logseq.order-list-type:: number
		- 创建并设置责任链。
		- 发出请求，并将请求传递给责任链的第一个处理程序。
- ### 责任链模式的关键特点：
	- **松耦合**：请求的发送者与处理程序之间的[[耦合度]]较低，发送者不需要知道处理程序的具体结构。
	- **灵活性**：可以动态添加或删除处理程序，并且可以轻松更改处理程序的顺序。
	- **增强扩展性**：通过添加新的处理程序，责任链可以扩展到处理新的请求。
- ### 示例代码：
  以下是使用 C++ 实现责任链模式的一个示例，展示了一个日志系统，其中不同级别的日志消息由不同的处理程序处理。
  ```cpp
  #include <iostream>
  #include <string>
  #include <memory>
  
  // 处理程序接口
  class Logger {
  protected:
    std::unique_ptr<Logger> nextLogger;  // 下一个处理程序
  
  public:
    virtual ~Logger() {}
  
    void setNextLogger(std::unique_ptr<Logger> next) {
        nextLogger = std::move(next);
    }
  
    void logMessage(const std::string& message, int level) {
        if (canHandle(level)) {
            handle(message);
        } else if (nextLogger) {
            nextLogger->logMessage(message, level);
        }
    }
  
  protected:
    virtual bool canHandle(int level) const = 0;
    virtual void handle(const std::string& message) = 0;
  };
  
  // 具体处理程序：信息日志
  class InfoLogger : public Logger {
  protected:
    bool canHandle(int level) const override {
        return level <= 1;  // 处理低级别日志
    }
  
    void handle(const std::string& message) override {
        std::cout << "INFO: " << message << std::endl;
    }
  };
  
  // 具体处理程序：警告日志
  class WarningLogger : public Logger {
  protected:
    bool canHandle(int level) const override {
        return level == 2;  // 处理中级别日志
    }
  
    void handle(const std::string& message) override {
        std::cout << "WARNING: " << message << std::endl;
    }
  };
  
  // 具体处理程序：错误日志
  class ErrorLogger : public Logger {
  protected:
    bool canHandle(int level) const override {
        return level >= 3;  // 处理高级别日志
    }
  
    void handle(const std::string& message) override {
        std::cout << "ERROR: " << message << std::endl;
    }
  };
  
  // 客户端代码
  int main() {
    auto errorLogger = std::make_unique<ErrorLogger>();
    auto warningLogger = std::make_unique<WarningLogger>();
    auto infoLogger = std::make_unique<InfoLogger>();
  
    // 创建责任链
    infoLogger->setNextLogger(std::move(warningLogger));
    infoLogger->setNextLogger(std::move(errorLogger));
  
    infoLogger->logMessage("This is an information.", 1);  // INFO
    infoLogger->logMessage("This is a warning.", 2);  // WARNING
    infoLogger->logMessage("This is an error.", 3);  // ERROR
  
    return 0;
  }
  ```
  在这个示例中，`Logger` 是处理程序接口，包含一个指向下一个处理程序的引用。`InfoLogger`、`WarningLogger`、`ErrorLogger` 是具体处理程序，每个处理程序根据日志级别处理请求。如果当前处理程序不能处理请求，它会将请求传递给下一个处理程序。
- ### 使用场景：
	- 当需要避免请求的发送者与处理程序之间的紧密耦合时。
	- 当需要动态设置或更改处理程序的顺序时。
	- 当请求处理的条件可以多种方式组合时。
- ### 注意事项：
	- **潜在的请求丢失**：如果责任链没有正确终止，可能导致请求无法得到处理。
	- **过度复杂**：责任链过长可能导致系统复杂度增加，并难以调试。
- 责任链模式通过创建一系列处理程序，使得请求可以在链上顺序传递，直到找到适合处理请求的处理程序。这提供了一种灵活的方式来处理不同类型的请求，适用于需要动态设置和修改请求处理逻辑的场景。