alias:: 解释器模式, 解析器模式

- ^^解释器模式^^（Interpreter Pattern）是一种[[行为型设计模式]]，提供了解析和执行特定语言或表达式的方法。通过解释器模式，你可以**定义一种语言的语法和规则，然后通过解释器对该语言进行解析和执行**。解释器模式在处理[[特定领域语言]]（Domain-Specific Language, DSL）、表达式计算、文档分析等领域非常有用。
- ### 解释器模式的组成：
	- **抽象表达式（Abstract Expression）**：
	  logseq.order-list-type:: number
		- 定义用于解释的接口，包括 `interpret(Context)` 方法。
	- **终结符表达式（Terminal Expression）**：
	  logseq.order-list-type:: number
		- 实现抽象表达式接口，表示语言中的终结符，如常量、变量等。
	- **非终结符表达式（Non-Terminal Expression）**：
	  logseq.order-list-type:: number
		- 实现抽象表达式接口，表示语言中的非终结符，如运算符、语法结构等。
		- 非终结符表达式通常包含一个或多个子表达式。
	- **上下文（Context）**：
	  logseq.order-list-type:: number
		- 提供解释过程中所需的环境信息，如变量值、输入数据等。
	- **客户端（Client）**：
	  logseq.order-list-type:: number
		- 创建解释器，并通过解释器解析和执行表达式。
- ### 解释器模式的关键特点：
	- **定义语言规则**：解释器模式允许定义一种语言的语法和规则，并通过解释器进行解析和执行。
	- **灵活的解析**：可以根据需求添加新的终结符或非终结符表达式，实现灵活的解析和执行。
	- **递归结构**：解释器模式适用于递归解析结构，如树状或嵌套结构。
- ### 示例代码：
  以下是使用 C++ 实现解释器模式的一个示例，展示了一个简单的算术表达式解释器。
  ```cpp
  #include <iostream>
  #include <memory>
  #include <map>
  #include <string>
  
  // 上下文
  class Context {
  public:
    std::map<std::string, int> variables;
  
    int getVariable(const std::string& name) {
        return variables[name];
    }
  
    void setVariable(const std::string& name, int value) {
        variables[name] = value;
    }
  };
  
  // 抽象表达式
  class Expression {
  public:
    virtual ~Expression() {}
    virtual int interpret(const Context& context) const = 0;
  };
  
  // 终结符表达式：常量
  class ConstantExpression : public Expression {
  private:
    int value;
  
  public:
    ConstantExpression(int v) : value(v) {}
  
    int interpret(const Context& context) const override {
        return value;
    }
  };
  
  // 终结符表达式：变量
  class VariableExpression : public Expression {
  private:
    std::string name;
  
  public:
    VariableExpression(const std::string& n) : name(n) {}
  
    int interpret(const Context& context) const override {
        return context.getVariable(name);
    }
  };
  
  // 非终结符表达式：加法
  class AddExpression : public Expression {
  private:
    std::shared_ptr<Expression> left;
    std::shared_ptr<Expression> right;
  
  public:
    AddExpression(std::shared_ptr<Expression> l, std::shared_ptr<Expression> r)
        : left(l), right(r) {}
  
    int interpret(const Context& context) const override {
        return left->interpret(context) + right->interpret(context);
    }
  };
  
  // 客户端代码
  int main() {
    Context context;
    context.setVariable("x", 10);
    context.setVariable("y", 20);
  
    // 表达式：x + y
    auto expression = std::make_shared<AddExpression>(
        std::make_shared<VariableExpression>("x"),
        std::make_shared<VariableExpression>("y")
    );
  
    std::cout << "Result: " << expression->interpret(context) << std::endl;  // 输出: Result: 30
  
    return 0;
  }
  ```
  在这个示例中，`Expression` 是抽象表达式接口，`ConstantExpression` 和 `VariableExpression` 是终结符表达式，`AddExpression` 是非终结符表达式，`Context` 提供解释过程中所需的环境信息。客户端通过 `interpret` 方法解析和执行表达式。
- ### 使用场景：
	- 当需要解析和执行特定语言或表达式时。
	- 当需要定义一种特定领域语言（DSL）并实现其解析和执行时。
	- 当对象结构是递归的，如树状结构，且需要递归解析时。
- ### 注意事项：
	- **复杂性**：解释器模式可能导致代码复杂性增加，特别是处理复杂的语言结构时。
	- **性能问题**：解释器模式可能导致性能问题，特别是解析复杂结构或大型数据集时。
- 解释器模式提供了一种灵活的方式来解析和执行特定语言或表达式，适用于需要定义和解析特定领域语言或复杂表达式的场景。