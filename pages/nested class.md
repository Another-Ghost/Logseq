alias:: 嵌套类, 内部类

- 在 C++ 中，[[嵌套类]]是定义在另一个类内部的类。
  这种类结构使得[[内部类]]**可以访问[[外部类]]的成员，包括[[私有成员]]**，而外部类则需要内部类的实例来访问其成员。
  嵌套类常用于组织和封装与外部类密切相关的功能。
- ### 嵌套类的特点
	- 1. **访问控制**：嵌套类可以访问外部类的所有成员（包括私有和保护成员），但外部类不能直接访问嵌套类的成员。
	- 2. **作用域**：嵌套类的名称在外部类的作用域内。要在外部类之外引用嵌套类，需要使用外部类的名称作为[[限定符]]（比如 `OuterClass::NestedClass`）。
	- id:: 65993ae3-c894-4a17-9bf0-e3c8206be5f6
	  3. **独立实例**：嵌套类的实例是独立于外部类实例的。创建嵌套类的实例**不需要外部类的实例**。
- ### 示例代码
  
  ```cpp
  class OuterClass {
  public:
    int x;
  
    class NestedClass {	//定义也可以在类外
    public:
        void display(OuterClass& outer) {
            std::cout << "OuterClass x is " << outer.x << std::endl;
        }
    };
  };
  
  int main() {
    OuterClass outer;
    outer.x = 10;
  
    OuterClass::NestedClass nested;
    nested.display(outer);  // 输出：OuterClass x is 10
  
    return 0;
  }
  ```
  
  在此示例中，`NestedClass` 是定义在 `OuterClass` 内部的嵌套类。嵌套类 `NestedClass` 可以访问 `OuterClass` 的成员 `x`。
- ### 使用场景
  嵌套类在以下情况中特别有用：
	- 当一个类（嵌套类）只在另一个类（外部类）的上下文中有意义时。
	  id:: 65993a1a-47aa-4b11-9e72-1541c84179e6
	- 用于实现特定的内部机制，同时**不希望这些机制对外部类的用户可见**，从而保持外部类接口的简洁性。
	- 在设计模式中，如[[工厂模式]]和[[迭代器模式]]，嵌套类可以用来实现这些模式。