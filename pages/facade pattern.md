alias:: 外观模式, 门面模式

- 外观模式（Facade Pattern）是一种[[结构型设计模式]]，它**提供了一个统一的接口，用于隐藏复杂系统的内部细节，并简化客户端与复杂系统的交互**。外观模式通常用于创建一个高级接口，该接口封装了系统内部的复杂性，使得客户端可以通过简单的调用与复杂系统交互，而不需要深入了解内部实现。
- ### 外观模式的组成：
	- **外观（Facade）**：
	  logseq.order-list-type:: number
		- 定义了一个简化的接口，用于与复杂系统交互。
		- 外观内部包含对复杂系统的引用，并将客户端的请求转发到适当的内部组件。
	- **子系统（Subsystem）**：
	  logseq.order-list-type:: number
		- 构成复杂系统的组件，每个子系统执行一部分任务。
		- 子系统可能相互依赖，但在外观模式中，客户端只与外观交互，而不直接访问子系统。
- ### 外观模式的关键特点：
	- **简化客户端交互**：提供一个简化的接口，使得客户端不需要了解系统内部的复杂性。
	- **减少耦合**：客户端与复杂系统之间的耦合通过外观得到简化。
	- **组织代码**：外观可以作为复杂系统的入口点，帮助组织代码和模块。
- ### 示例代码：
  
  以下是使用 C++ 实现外观模式的一个简单示例，展示了一个家庭影院系统的外观。
  
  ```cpp
  #include <iostream>
  
  // 子系统1：投影仪
  class Projector {
  public:
    void on() {
        std::cout << "Projector is on.\n";
    }
    void off() {
        std::cout << "Projector is off.\n";
    }
  };
  
  // 子系统2：音响系统
  class SoundSystem {
  public:
    void turnOn() {
        std::cout << "Sound system is turned on.\n";
    }
    void turnOff() {
        std::cout << "Sound system is turned off.\n";
    }
  };
  
  // 子系统3：DVD 播放器
  class DVDPlayer {
  public:
    void play() {
        std::cout << "DVD player is playing.\n";
    }
    void stop() {
        std::cout << "DVD player has stopped.\n";
    }
  };
  
  // 外观类
  class HomeTheaterFacade {
  private:
    Projector projector;
    SoundSystem soundSystem;
    DVDPlayer dvdPlayer;
  
  public:
    void watchMovie() {
        std::cout << "Getting ready to watch a movie...\n";
        projector.on();
        soundSystem.turnOn();
        dvdPlayer.play();
    }
  
    void endMovie() {
        std::cout << "Shutting down the movie...\n";
        dvdPlayer.stop();
        soundSystem.turnOff();
        projector.off();
    }
  };
  
  int main() {
    HomeTheaterFacade homeTheater;
  
    homeTheater.watchMovie();  // 一次性启动所有子系统
    homeTheater.endMovie();    // 一次性关闭所有子系统
  
    return 0;
  }
  ```
- ### 使用场景：
	- 当你想提供一个简化的接口来隐藏系统的复杂性时。
	- 当你想减少客户端和复杂系统之间的耦合时。
	- 当系统内部的组件或子系统可能发生变化，而不希望影响客户端时。
- ### 注意事项：
	- **责任隔离**：外观应尽量保持简单，只提供简化的接口，而不应承担过多的责任。
	- **过度封装**：外观不应完全掩盖系统的复杂性，否则**可能会限制客户端的灵活性**。
- 外观模式通过提供一个统一的接口，将复杂系统的内部细节隐藏起来，为客户端提供了简化和统一的交互方式。这有助于提高代码的可维护性和可扩展性。