alias:: 备忘录模式

- ^^备忘录模式^^（Memento Pattern）是一种[[行为型设计模式]]，用于在不破坏封装的情况下保存和恢复对象的状态。这个模式非常适用于需要提供撤销、回滚功能，或者需要记录对象历史状态的场景。通过备忘录模式，客户端可以恢复对象到之前的某个状态，而不必暴露对象的内部结构。
- ### 备忘录模式的组成：
	- **发起者（Originator）**：
	  logseq.order-list-type:: number
		- 代表具有^^内部状态^^的对象。
		- 可以创建备忘录，以保存当前状态。
		- 可以使用备忘录来恢复以前的状态。
	- **备忘录（Memento）**：
	  logseq.order-list-type:: number
		- 存储发起者的状态。
		- 备忘录不应该暴露发起者的内部状态，以保证封装性。
	- **看管者（Caretaker）**：
	  logseq.order-list-type:: number
		- 负责保存备忘录。
		- 可以管理备忘录的历史，允许发起者恢复到之前的状态。
		- 看管者不直接访问备忘录的内容。
- ### 备忘录模式的关键特点：
	- **封装性**：备忘录不应暴露发起者的内部状态，这样可以确保对象的封装。
	- **状态恢复**：备忘录模式允许对象在不暴露内部状态的情况下保存和恢复状态。
	- **支持撤销和回滚**：备忘录模式可以用于提供撤销和回滚功能。
- ### 示例代码：
  以下是使用 C++ 实现备忘录模式的一个示例，展示了如何保存和恢复一个对象的状态。
  ```cpp
  #include <iostream>
  #include <vector>
  #include <string>
  
  // 备忘录类
  class Memento {
  private:
    std::string state; // 备忘录存储的状态
  public:
    Memento(const std::string& s) : state(s) {}
    
    std::string getState() const {
        return state;
    }
  };
  
  // 发起者
  class Originator {
  private:
    std::string state; // 当前状态
  public:
    void setState(const std::string& s) {
        state = s;
    }
    std::string getState() const {
        return state;
    }
    Memento saveStateToMemento() const {
        return Memento(state);
    }
    void restoreStateFromMemento(const Memento& memento) {
        state = memento.getState();
    }
  };
  
  // 看管者
  class Caretaker {
  private:
    std::vector<Memento> mementos; // 备忘录历史记录
  public:
    void addMemento(const Memento& memento) {
        mementos.push_back(memento);
    }
    Memento getMemento(int index) const {
        if (index >= 0 && index < mementos.size()) {
            return mementos[index];
        }
        throw std::out_of_range("Invalid index");
    }
  };
  
  // 客户端代码
  int main() {
    Originator originator;
    Caretaker caretaker;
  
    originator.setState("State1");
    caretaker.addMemento(originator.saveStateToMemento());
  
    originator.setState("State2");
    caretaker.addMemento(originator.saveStateToMemento());
  
    originator.setState("State3");
  
    std::cout << "Current state: " << originator.getState() << std::endl;
  
    // 恢复到之前的状态
    originator.restoreStateFromMemento(caretaker.getMemento(1));
    std::cout << "Restored state: " << originator.getState() << stdendl;
  
    originator.restoreStateFromMemento(caretaker.getMemento(0));
    std::cout << "Restored state: " << originator.getState() << std::endl;
  
    return 0;
  }
  ```
  
  在这个示例中，`Originator` 是具有内部状态的对象，`Caretaker` 管理 `Memento` 对象的历史记录。通过 `Memento`，`Originator` 可以保存和恢复状态，而不暴露其内部结构。
- ### 使用场景：
	- 当你需要提供撤销或回滚功能时。
	- 当你需要在不破坏封装的情况下保存和恢复对象状态时。
- ### 注意事项：
	- **内存开销**：备忘录模式可能会导致较高的内存开销，特别是当备忘录保存的数据量较大时。
	- **过度使用**：不应过度使用备忘录模式，否则可能导致系统变得复杂。
- 备忘录模式通过提供一种安全的方式来保存和恢复对象状态，有助于实现撤销和回滚等功能，而不会破坏对象的封装性。