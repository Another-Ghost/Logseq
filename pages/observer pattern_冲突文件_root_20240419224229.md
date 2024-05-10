alias:: 观察者模式

- 观察者模式（Observer Pattern）是一种非常流行的软件设计模式，属于[[行为型模式]]。这种模式用于建立一种对象与其依赖对象之间的一对多的依赖关系，以便当一个对象改变状态时，所有**依赖于它的对象都会收到通知并自动更新**。这种模式通常用于实现分布式事件处理系统，其中对象之间的这种松散耦合是必需的。
- ### 观察者模式的组成：
	- **主题（Subject）**：
	  logseq.order-list-type:: number
		- 主题持有观察者的列表，可以添加或删除观察者对象。
		- 当主题的状态发生变化时，主题会通知所有的观察者。
	- **观察者（Observer）**：
	  logseq.order-list-type:: number
		- 观察者接口定义了接收到通知时调用的更新方法。
		- 所有具体的观察者类都需要实现这个接口，并定义在接收到通知时如何更新自己。
	- **具体主题（Concrete Subject）**：
	  logseq.order-list-type:: number
		- 继承或实现主题，包含具体要被观察的状态。
		- 当状态改变时，触发通知所有注册的观察者。
	- **具体观察者（Concrete Observer）**：
	  logseq.order-list-type:: number
		- 实现观察者接口的类，定义当接收到主题状态变化通知时的具体行为。
	- ((66227e3d-a322-42cb-9341-26298ab7c563))
- ### 观察者模式的关键特点：
	- **解耦**：主题（发布者）与观察者（订阅者）之间不必紧密耦合，主题不需要知道观察者的具体类，只知道观察者实现了观察者接口。
	- **实时更新**：允许实时通知所有关注主题状态变化的观察者，实现动态更新。
- ### 示例代码：
  下面是 C++ 中实现观察者模式的一个简单示例，演示一个新闻服务（主题）和两种类型的订阅者（观察者）：
  ```cpp
  #include <iostream>
  #include <vector>
  #include <string>
  
  // 观察者接口
  class Observer {
  public:
    virtual ~Observer() {}
    virtual void update(const std::string &message) = 0;
  };
  
  // 主题接口
  class Subject {
  public:
    virtual ~Subject() {}
    virtual void attach(Observer *observer) = 0;
    virtual void detach(Observer *observer) = 0;
    virtual void notify() = 0;
  };
  
  // 具体主题
  class NewsPublisher : public Subject {
  private:
    std::vector<Observer*> observers;
    std::string news;
  
  public:
    void attach(Observer *observer) override {
        observers.push_back(observer);
    }
  
    void detach(Observer *observer) override {
        observers.erase(std::remove(observers.begin(), observers.end(), observer), observers.end());
    }
  
    void notify() override {
        for (Observer *observer : observers) {
            observer->update(news);
        }
    }
  
    void publishNews(const std::string &news) {
        this->news = news;
        notify();
    }
  };
  
  // 具体观察者
  class EmailSubscriber : public Observer {
  public:
    void update(const std::string &message) override {
        std::cout << "Email Alert: " << message << std::endl;
    }
  };
  
  class SMSSubscriber : public Observer {
  public:
    void update(const std::string &message) override {
        std::cout << "SMS Alert: " << message << std::endl;
    }
  };
  
  int main() {
    NewsPublisher publisher;
    EmailSubscriber emailObserver;
    SMSSubscriber smsObserver;
  
    publisher.attach(&emailObserver);
    publisher.attach(&smsObserver);
  
    publisher.publishNews("Breaking News: Observer Pattern in C++");
  
    publisher.detach(&smsObserver);
  
    publisher.publishNews("More News: Observer Pattern Example");
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当一个抽象模型有两个方面，其中一个方面依赖于另一个方面时。将这些方面封装在
	  独立的对象中可以使它们可以各自独立地改变和复用。
	- 当对一个对象的改变需要同时改变其他对象，而不知道具体有多少对象需要改变时。
	- 当一个对象应该能够通知其他对象，而又不应该假设这些对象是谁。
	  通过使用观察者模式，可以有效地建立一个触发机制，促使每当对象发生改变时，其相关依赖对象会收到通知并自动更新。这种模式广泛应用于实时数据处理系统、事件管理系统等领域。
	  <!--Converted by ToLogseq-->