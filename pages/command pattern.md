alias:: 命令模式

- [[命令模式]]（Command Pattern）是一种[[行为型设计模式]]，它**将请求或操作封装为对象，以便在不同的上下文中传递、存储、撤销或排队**。命令模式提供了一种松耦合的方式来处理请求，使请求的发送者与执行者分离，允许请求的参数化、延迟执行、撤销/重做等功能。
- ### 命令模式的组成：
	- **命令接口（Command Interface）**：
	  logseq.order-list-type:: number
		- 定义执行^^请求^^的接口，包括一个 `execute()` 方法。
	- **具体命令（Concrete Command）**：
	  logseq.order-list-type:: number
		- 实现命令接口，封装了对接收者的引用和相关操作。
	- **接收者（Receiver）**：
	  logseq.order-list-type:: number
		- 执行请求的对象，包含具体的操作逻辑。
	- **调用者（Invoker）**：
	  logseq.order-list-type:: number
		- 触发命令的对象，通常是用户界面控件、按钮或其他触发事件。
	- **客户端（Client）**：
	  logseq.order-list-type:: number
		- 创建具体命令，并将其关联到接收者。
- ### 命令模式的关键特点：
	- **松耦合**：请求的发送者和执行者通过命令分离，允许更灵活的请求处理。
	- **参数化请求**：可以通过命令传递参数，使请求更加灵活。
	- **支持撤销/重做**：通过命令对象可以实现撤销和重做操作。
- ### 示例代码：
  以下是使用 C++ 实现命令模式的一个示例，展示了一个简单的遥控器系统，可以通过命令对象来控制灯的开关。
  ```cpp
  #include <iostream>
  #include <memory>
  
  // 命令接口
  class Command {
  public:
    virtual ~Command() {}
    virtual void execute() = 0;
  };
  
  // 接收者
  class Light {
  public:
    void turnOn() {
        std::cout << "Light is ON.\n";
    }
  
    void turnOff() {
        std::cout << "Light is OFF.\n";
    }
  };
  
  // 具体命令：开灯命令
  class LightOnCommand : public Command {
  private:
    Light& light;
  
  public:
    LightOnCommand(Light& l) : light(l) {}
  
    void execute() override {
        light.turnOn();
    }
  };
  
  // 具体命令：关灯命令
  class LightOffCommand : public Command {
  private:
    Light& light;
  
  public:
    LightOffCommand(Light& l) : light(l) {}
  
    void execute() override {
        light.turnOff();
    }
  };
  
  // 调用者
  class RemoteControl {
  private:
    std::unique_ptr<Command> command;
  
  public:
    void setCommand(std::unique_ptr<Command> cmd) {
        command = std::move(cmd);
    }
  
    void pressButton() {
        if (command) {
            command->execute();
        }
    }
  };
  
  // 客户端代码
  int main() {
    Light livingRoomLight;
  
    RemoteControl remote;
  
    // 设置开灯命令
    remote.setCommand(std::make_unique<LightOnCommand>(livingRoomLight));
    remote.pressButton();  // 输出: Light is ON.
  
    // 设置关灯命令
    remote.setCommand(std::make_unique<LightOffCommand>(livingRoomLight));
    remote.pressButton();  // 输出: Light is OFF.
  
    return 0;
  }
  ```
  在这个示例中，`Light` 是接收者，包含灯的开关操作。`LightOnCommand` 和 `LightOffCommand` 是具体命令，封装了对接收者的引用和操作逻辑。`RemoteControl` 是调用者，通过 `setCommand` 设置命令，通过 `pressButton` 执行命令。客户端通过 `RemoteControl` 控制灯的开关，而不必直接与 `Light` 交互。
- ### 使用场景：
	- 当你需要将请求和执行分离，以实现松耦合时。
	- 当你需要支持撤销/重做操作时。
	- 当请求需要排队、记录日志、参数化等功能时。
- ### 注意事项：
	- **过度设计**：如果请求处理逻辑简单，可能不需要命令模式。
	- **复杂性**：命令模式可能增加代码的复杂性，特别是涉及大量命令时。
- 命令模式提供了一种灵活的方式来处理请求，适用于需要松耦合、参数化请求、支持撤销/重做等功能的场景。
-