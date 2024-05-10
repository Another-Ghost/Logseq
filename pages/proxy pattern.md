alias:: 代理模式

- 代理模式（Proxy Pattern）是一种结构型设计模式，它允许在不改变目标对象接口的情况下，通过代理对象来控制对目标对象的访问。代理模式通过在目标对象和客户端之间插入代理，提供了附加的功能，如控制访问权限、延迟初始化、缓存、日志记录、监控等。
- ### 代理模式的组成：
	- **对象接口（Subject Interface）**：
	  logseq.order-list-type:: number
		- 定义了 Real Subject 和 Proxy 应当实现的接口，这样 Proxy 就可以用来替代 Real Subject。
		  logseq.order-list-type:: number
	- **实际对象（Real Subject）**：
	  logseq.order-list-type:: number
		- 代理所代表的实际对象。目标对象实现了实际的操作逻辑。
	- **代理对象（Proxy）**：
	  logseq.order-list-type:: number
		- 代理对象实现与目标对象相同的接口，封装了对目标对象的访问。
		- 代理对象可以在访问目标对象之前或之后执行额外的操作。
	- **客户端（Client）**：
	  logseq.order-list-type:: number
		- 与代理对象交互，而不直接访问目标对象。
- ### 代理模式的关键特点：
	- **控制访问**：代理可以控制对目标对象的访问，并可以根据需要实现附加的功能。
	- **延迟初始化**：代理可以**延迟目标对象的创建**，以提高性能。
	- **附加功能**：代理可以在调用目标对象前后添加日志、缓存、监控等功能。
- ### 示例代码：
  
  以下是使用 C++ 实现代理模式的一个示例，展示了一个保护代理，控制对敏感资源的访问。
  
  ```cpp
  #include <iostream>
  #include <string>
  
  // 接口
  class Subject {
  public:
    virtual ~Subject() {}
    virtual void request() = 0;
  };
  
  // 实际对象
  class RealSubject : public Subject {
  public:
    void request() override {
        std::cout << "RealSubject: Handling request.\n";
    }
  };
  
  // 代理对象
  class Proxy : public Subject {
  private:
    RealSubject* realSubject;
    std::string password;
  
  public:
    Proxy(const std::string& pwd) : realSubject(nullptr), password(pwd) {}
  
    ~Proxy() {
        delete realSubject;
    }
  
    void request() override {
        if (checkAccess()) {
            if (!realSubject) {
                realSubject = new RealSubject();
            }
            realSubject->request();
            logAccess();
        } else {
            std::cout << "Proxy: Access denied.\n";
        }
    }
  
  private:
    bool checkAccess() {
        std::string enteredPassword;
        std::cout << "Enter password to access RealSubject: ";
        std::cin >> enteredPassword;
        return enteredPassword == password;
    }
  
    void logAccess() {
        std::cout << "Proxy: Logging the access.\n";
    }
  };
  
  int main() {
    Proxy proxy("securePassword");
  
    proxy.request();  // 请求由代理控制，检查权限
    return 0;
  }
  ```
  
  在这个示例中，代理对象 `Proxy` 控制对 `RealSubject` 的访问，并在访问前检查密码。在满足访问条件后，代理对象可以延迟初始化 `RealSubject` 并处理额外的日志记录。
- ### 使用场景：
	- 当你需要控制对敏感资源的访问时，例如保护代理。
	- 当你需要延迟目标对象的初始化以提高性能时，例如虚拟代理。
	- 当你想在访问目标对象前后添加额外的功能时，例如日志记录、监控或缓存。
- ### 注意事项：
	- **延迟初始化**：代理模式可以延迟被代理对象的创建时间，直到实际需要时，从而提高应用性能。
	- **透明代理**：理想情况下，代理应该对客户端透明，除非有明确的需求使得客户需要直接与代理交互。
- 代理模式为控制对象的访问提供了一种灵活的方法，使得在必要时可以添加各种功能，如安全性检查、延迟初始化、日志记录等。