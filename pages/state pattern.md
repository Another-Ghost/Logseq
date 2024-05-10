alias:: 状态模式

- 状态模式（State Pattern）是一种[[行为型设计模式]]，用于将对象的行为根据其内部状态进行改变。这种模式**允许对象在不同状态之间进行转换**，每个状态都有自己的行为。状态模式有助于消除复杂条件语句，并提高系统的可扩展性和可维护性。
- ### 状态模式的组成：
	- **状态接口（State Interface）**：
	  logseq.order-list-type:: number
		- 定义不同状态下的行为。所有具体状态类都实现这个接口。
	- **具体状态类（Concrete State Classes）**：
	  logseq.order-list-type:: number
		- 实现状态接口，每个具体状态都有自己的行为实现。
	- **上下文（Context）**：
	  logseq.order-list-type:: number
		- 上下文持有当前状态的引用，并允许在不同状态之间进行转换。
		- 上下文可以委托行为给当前状态对象。
- ### 状态模式的关键特点：
	- **消除复杂条件语句**：通过状态对象的转换，**避免了使用大量条件语句来处理不同状态**。
	- **行为封装**：每个状态的行为被封装在具体状态类中，提高了代码的可维护性和可扩展性。
	- **易于扩展**：通过添加新的状态类，可以轻松扩展系统的行为。
- ### 示例代码：
  以下是使用 C++ 实现状态模式的一个示例，展示了一个文档的状态转换，包括草稿、审核和发布等状态。
  ```cpp
  #include <iostream>
  #include <memory>
  #include <string>
  
  // 状态接口
  class State {
  public:
    virtual ~State() {}
    virtual void publish() = 0;
    virtual void edit() = 0;
  };
  
  // 上下文
  class Document {
  private:
    std::unique_ptr<State> state;
  
  public:
    Document(std::unique_ptr<State> initialState) : state(std::move(initialState)) {}
  
    void setState(std::unique_ptr<State> newState) {
        state = std::move(newState);
    }
  
    void publish() {
        state->publish();
    }
  
    void edit() {
        state->edit();
    }
  };
  
  // 具体状态类：草稿状态
  class DraftState : public State {
  private:
    Document* document;
  
  public:
    DraftState(Document* doc) : document(doc) {}
  
    void publish() override {
        std::cout << "Draft published.\n";
        document->setState(std::make_unique<ReviewState>(document));
    }
  
    void edit() override {
        std::cout << "Editing draft.\n";
    }
  };
  
  // 具体状态类：审核状态
  class ReviewState : public State {
  private:
    Document* document;
  
  public:
    ReviewState(Document* doc) : document(doc) {}
  
    void publish() override {
        std::cout << "Under review, can't publish.\n";
    }
  
    void edit() override {
        std::cout << "Editing during review.\n";
    }
  };
  
  // 具体状态类：发布状态
  class PublishedState : public State {
  private:
    Document* document;
  
  public:
    PublishedState(Document* doc) : document(doc) {}
  
    void publish() override {
        std::cout << "Already published.\n";
    }
  
    void edit() override {
        std::cout << "Can't edit published document.\n";
    }
  };
  
  int main() {
    Document doc(std::make_unique<DraftState>(nullptr));
  
    doc.edit();  // 输出: Editing draft.
    doc.publish();  // 输出: Draft published. (转为 ReviewState)
    doc.edit();  // 输出: Editing during review.
    doc.publish();  // 输出: Under review, can't publish.
    doc.setState(std::make_unique<PublishedState>(nullptr));
    doc.publish();  // 输出: Already published.
    doc.edit();  // 输出: Can't edit published document.
  
    return 0;
  }
  ```
  
  在这个示例中，`Document` 是上下文，持有当前状态的引用。不同的状态类实现了各自的行为，例如 `DraftState` 可以编辑和发布，而 `ReviewState` 只能编辑，`PublishedState` 不能编辑。通过 `setState` 方法，`Document` 可以在不同状态之间进行转换。
- ### 使用场景：
	- 当对象的行为依赖于其状态，并且需要在不同状态之间进行转换时。
	- 当需要消除复杂条件语句，并通过封装状态来简化代码时。
- ### 注意事项：
	- **过度设计**：如果状态转换逻辑简单，可能不需要状态模式。
	- **状态爆炸**：如果状态太多，可能会导致代码复杂性增加。
- 状态模式提供了一种优雅的方式来处理对象的状态转换和行为变化，适用于对象的行为根据内部状态发生显著变化的场景。