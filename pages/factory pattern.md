alias:: 工厂模式

- 工厂模式（Factory Pattern）是一种[[创建型设计模式]]，它提供了一种创建对象的最佳方式。在工厂模式中，我们在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个共同的接口来指向新创建的对象。工厂模式主要分为两种：[[简单工厂模式]]（Simple Factory）和[[工厂方法模式]]（Factory Method）。
- ### 工厂方法模式（Factory Method）
  工厂方法模式定义了一个创建对象的接口，但让子类决定要实例化的类是哪一个。工厂方法让类的实例化推迟到子类中进行。
- #### 示例场景
  假设我们有一个应用，需要根据不同的文件类型（如文本文件、图像文件等）来创建不同的解析器对象。每种文件类型的解析器都有不同的解析逻辑。
- #### C++ 实现
  首先，我们定义一个抽象的解析器接口（`Parser`），然后为每种文件类型实现一个具体的解析器类。最后，我们创建一个工厂类，根据输入的文件类型返回对应的解析器对象。
  
  ```cpp
  #include <iostream>
  #include <memory>
  
  // 抽象产品类
  class Parser {
  public:
    virtual ~Parser() {}
    virtual void parse() = 0;
  };
  
  // 具体产品类：文本文件解析器
  class TextParser : public Parser {
  public:
    void parse() override {
        std::cout << "Parsing text file..." << std::endl;
    }
  };
  
  // 具体产品类：图像文件解析器
  class ImageParser : public Parser {
  public:
    void parse() override {
        std::cout << "Parsing image file..." << std::endl;
    }
  };
  
  // 抽象工厂类
  class ParserFactory {
  public:
    virtual ~ParserFactory() {}
    virtual std::unique_ptr<Parser> createParser() = 0;
  };
  
  // 具体工厂类：文本文件解析器工厂
  class TextParserFactory : public ParserFactory {
  public:
    std::unique_ptr<Parser> createParser() override {
        return std::make_unique<TextParser>();
    }
  };
  
  // 具体工厂类：图像文件解析器工厂
  class ImageParserFactory : public ParserFactory {
  public:
    std::unique_ptr<Parser> createParser() override {
        return std::make_unique<ImageParser>();
    }
  };
  
  // 客户端代码
  int main() {
    std::unique_ptr<ParserFactory> factory = std::make_unique<TextParserFactory>();
    std::unique_ptr<Parser> parser = factory->createParser();
    parser->parse();
  
    factory = std::make_unique<ImageParserFactory>();
    parser = factory->createParser();
    parser->parse();
  
    return 0;
  }
  ```
  
  在这个例子中，`ParserFactory`是一个抽象工厂类，它定义了一个`createParser`方法。`TextParserFactory`和`ImageParserFactory`是具体的工厂类，它们实现了`createParser`方法来创建对应类型的解析器对象。客户端代码仅通过工厂接口与解析器对象交互，而不需要知道具体的解析器类，这样就实现了解耦和灵活性。
  
  工厂模式在C++中的应用非常广泛，特别是在需要根据不同条件创建不同对象时，它提供了一种清晰、灵活的方式来实现对象的创建和管理。
-