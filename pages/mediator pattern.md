alias:: 中介者模式

- 中介者模式（Mediator Pattern）是一种[[行为型设计模式]]，它用于减少对象之间的直接交互，避免过度耦合。通过**引入一个中介者对象，所有对象之间的通信都通过中介者进行**，从而使得对象之间的依赖关系更加松散，这有助于维护和扩展系统。
- ### 中介者模式的组成：
	- **中介者接口（Mediator Interface）**：
	  logseq.order-list-type:: number
		- 定义一个用于与其他对象通信的接口。
	- **具体中介者（Concrete Mediator）**：
	  logseq.order-list-type:: number
		- 实现中介者接口，并协调多个同事对象之间的交互。
	- **同事对象（Colleague Objects）**：
	  logseq.order-list-type:: number
		- 实现中介者接口的对象，代表参与者。每个同事对象与中介者通信，而不与其他同事对象直接通信。
- ### 中介者模式的关键特点：
	- **减少耦合**：通过中介者对象，减少了对象之间的直接依赖，增强了系统的松耦合。
	- **简化交互**：中介者负责协调和管理对象之间的交互，这使得代码更加清晰和易于理解。
	- **灵活性**：中介者模式有助于在不影响其他同事对象的情况下修改或替换同事对象。
- ### 示例代码：
  
  以下是使用 C++ 实现中介者模式的一个示例，展示了一个聊天室的中介者，协调多个用户之间的交互。
  
  ```cpp
  #include <iostream>
  #include <string>
  #include <vector>
  
  // 中介者接口
  class Mediator {
  public:
    virtual ~Mediator() {}
    virtual void sendMessage(const std::string& message, class Colleague* sender) = 0;
    virtual void addColleague(class Colleague* colleague) = 0;
  };
  
  // 同事对象
  class Colleague {
  protected:
    Mediator* mediator;
    std::string name;
  
  public:
    Colleague(Mediator* m, const std::string& n) : mediator(m), name(n) {}
  
    virtual void receiveMessage(const std::string& message) {
        std::cout << name << " received: " << message << std::endl;
    }
  
    virtual void sendMessage(const std::string& message) {
        mediator->sendMessage(message, this);
    }
  };
  
  // 具体中介者
  class ChatMediator : public Mediator {
  private:
    std::vector<Colleague*> colleagues;
  
  public:
    void sendMessage(const std::string& message, Colleague* sender) override {
        for (Colleague* colleague : colleagues) {
            if (colleague != sender) {
                colleague->receiveMessage(message);
            }
        }
    }
  
    void addColleague(Colleague* colleague) override {
        colleagues.push_back(colleague);
    }
  };
  
  int main() {
    ChatMediator chat;
  
    Colleague user1(&chat, "User1");
    Colleague user2(&chat, "User2");
    Colleague user3(&chat, "User3");
  
    chat.addColleague(&user1);
    chat.addColleague(&user2);
    chat.addColleague(&user3);
  
    user1.sendMessage("Hello, everyone!");
    user2.sendMessage("Hi, User1!");
  
    return 0;
  }
  ```
  
  在这个示例中，`ChatMediator` 作为中介者，负责协调多个用户之间的消息传递。用户（同事对象）通过中介者发送和接收消息，而不是直接与其他用户通信。
- ### 使用场景：
	- 当你想减少对象之间的直接交互，以避免过度耦合时。
	- 当你需要管理和协调多个对象之间的复杂交互时。
	- 当系统的对象关系较为复杂，使用中介者可以简化和优化对象之间的交互。
- ### 注意事项：
	- **过度复杂**：中介者模式可能会导致中介者对象承担过多的责任，造成复杂性增加。
	- **过度依赖**：如果中介者变得过于复杂，可能会导致系统中其他部分过度依赖中介者，影响扩展和维护。
- 中介者模式提供了一种减少对象之间耦合的方法，通过引入中介者来协调对象之间的交互。这种模式在需要管理复杂交互关系的系统中非常有用。
  <!--Converted by ToLogseq-->