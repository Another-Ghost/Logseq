alias:: 装饰器模式

- 装饰器模式（Decorator Pattern）是一种[[结构型模式]]，它允许用户**在不修改现有对象的结构的情况下，向对象添加新的功能**。这种模式创建了一个装饰类，用来包装原有的类，并在**保持原类方法签名完整性**的前提下，提供了额外的功能。
- ### 装饰器模式的核心组成：
	- **组件接口（Component）**：
	  logseq.order-list-type:: number
		- 定义一个对象接口，可以动态地给这些对象添加职责（功能）。
	- **具体组件（Concrete Component）**：
	  logseq.order-list-type:: number
		- 是被装饰的原始对象，实现了组件接口。
	- **装饰类（Decorator）**：
	  logseq.order-list-type:: number
		- 维护一个指向组件对象的引用，并定义一个与组件接口一致的接口。
	- **具体装饰类（Concrete Decorators）**：
	  logseq.order-list-type:: number
		- 装饰具体组件，通过在调用原始对象的方法前后添加额外的行为来扩展对象的功能。
	- ((66239ec1-db4e-420f-8fe2-29ff2a261b00))
- ### 装饰器模式的关键特点：
	- **灵活性**：相较于继承，装饰器模式提供了更加灵活的方式来添加对象的功能，因为它可以在运行时添加和删除功能。
	- **扩展性**：允许通过添加新的装饰类在不改变现有代码的情况下引入新的行为。
	- **避免类爆炸**：通过使用装饰器，可以避免创建大量具有不同组合功能的类。
- ### 示例代码：
  以下是 C++ 中实现装饰器模式的一个示例，假设我们有一个文本消息的处理系统，需要根据不同的需求添加不同的处理功能（例如加密、压缩等）。
  ```cpp
  #include <iostream>
  #include <string>
  
  // 组件接口
  class Text {
  public:
    virtual ~Text() {}
    virtual std::string getText() const = 0;
  };
  
  // 具体组件
  class PlainText : public Text {
  private:
    std::string text;
  public:
    PlainText(const std::string& t) : text(t) {}
    std::string getText() const override {
        return text;
    }
  };
  
  // 装饰基类
  class TextDecorator : public Text {
  protected:
    Text* wrappedText;
  public:
    TextDecorator(Text* text) : wrappedText(text) {}
    virtual ~TextDecorator() {
        delete wrappedText;
    }
  };
  
  // 具体装饰类：加密
  class EncryptedText : public TextDecorator {
  public:
    EncryptedText(Text* text) : TextDecorator(text) {}
    std::string getText() const override {
        std::string encryptedText = wrappedText->getText();  // 假设的加密操作
        return "Encrypted[" + encryptedText + "]";
    }
  };
  
  // 具体装饰类：压缩
  class CompressedText : public TextDecorator {
  public:
    CompressedText(Text* text) : TextDecorator(text) {}
    std::string getText() const override {
        std::string compressedText = wrappedText->getText();  // 假设的压缩操作
        return "Compressed[" + compressedText + "]";
    }
  };
  
  int main() {
    Text* plainText = new PlainText("Hello, World!");
    Text* encrypted = new EncryptedText(plainText);
    Text* compressed = new CompressedText(encrypted);
  
    std::cout << "Original: " << plainText->getText() << std::endl;
    std::cout << "Encrypted: " << encrypted->getText() << std::endl;
    std::cout << "Compressed: " << compressed->getText() << std::endl;
  
    delete compressed;  // 注意：由于装饰器负责删除包装的对象，此处仅需要删除最外层的装饰器
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当需要给对象添加额外的功能，且这些功能可以动态地添加或撤销时。
	- 当扩展一个类的功能比创建子类更灵活时。
	- 当需要通过组合行为方式构建一组功能而非继承方式时。
- 装饰器模式通过将每个要添加的功能封装在一个装饰类中，然后通过这个装饰类包装原始对象，实现了功能的动态组合，增强了软件的灵活性和可维护性。
-