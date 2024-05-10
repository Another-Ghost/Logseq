alias:: 设计模式

- [[设计模式参考]]
- ^^Design Patterns^^主要描述的是：[[类]]与相互通信的[[对象]]之间的组织关系，包括它们的角色、职责、协作方式等方面。
- 设计模式（Design Patterns）是软件工程中的一套被广泛认可的解决特定问题的模板或范式。它们代表了最佳实践，这些实践是由经验丰富的面向对象软件开发者所发现并总结出来的。设计模式可以提高代码的可重用性、可读性和可维护性。在C++中实现设计模式可以帮助开发者更高效地解决常见的[[软件设计]]问题。
- ## 分类
- ### 从目的来看
  设计模式通常分为三大类：
	- 1. **[[创建型模式]]**（Creational Patterns）：这类模式提供了对象创建机制的最佳方式，增加了程序的灵活性和可复用性。
		- [[单例模式]]（Singleton Pattern）
		- [[建造者模式]]（Builder Pattern）
		- [[原型模式]]（Prototype Pattern）
		- [[工厂方法模式]]（Factory Method Pattern）
		- [[抽象工厂模式]]（Abstract Factory Pattern）
	- 2. **[[结构型模式]]**（Structural Patterns）：这类模式关注类和对象的组合，通过继承来组合接口或实现。
		- [[适配器模式]]（Adapter Pattern）
		- [[桥接模式]]（Bridge Pattern）
		- [[组合模式]]（Composite Pattern）
		- [[装饰器模式]]（Decorator Pattern）
		- [[外观模式]]（Facade Pattern）
		- [[享元模式]]（Flyweight Pattern）
		- [[代理模式]]（Proxy Pattern）
	- 3. **[[行为型模式]]**（Behavioral Patterns）：这类模式专注于对象之间的通信。
		- [[责任链模式]]（Chain of Responsibility Pattern）
		- [[命令模式]]（Command Pattern）
		- [[解释器模式]]（Interpreter Pattern）
		- [[迭代器模式]]（Iterator Pattern）
		- [[中介者模式]]（Mediator Pattern）
		- [[备忘录模式]]（Memento Pattern）
		- [[观察者模式]]（Observer Pattern）
		- [[状态模式]]（State Pattern）
		- [[策略模式]]（Strategy Pattern）
		- [[模板方法模式]]（Template Method Pattern）
		- [[访问者模式]]（Visitor Pattern）
- ### 从范围来看
	- ^^类模式^^处理[[类]]与[[子类]]的[[静态关系]]。
	- ^^对象模式^^处理[[对象]]间的[[动态关系]]。
- ### ((66226cec-a70b-4843-a5e7-0a7043a2bd2f))
- ### 从封装[[变化]]角度对模式分类
	- #### [[组件协作模式]]
	  collapsed:: true
		- [[template Method Pattern]]
		- [[strategy pattern]]
		- [[observer pattern]]
	- #### [[单一职责模式]]
		- [[decorator pattern]]
		- [[bridge pattern]]
	- #### [[对象创建模式]]
		- [[factory method pattern]]
		- [[abstract factory pattern]]
		- [[prototype pattern]]
		- [[builder pattern]]
	- #### [[对象性能模式]]
		- [[singleton pattern]]
		- [[flyweight pattern]]
	- #### [[接口隔离模式]]
		- [[facade pattern]]
		- [[proxy pattern]]
		- [[mediator pattern]]
		- [[adapter pattern]]
	- #### [[状态变换模式]]
		- [[memento pattern]]
		- [[state pattern]]
	- #### [[数据结构]]
		- [[composite pattern]]
		- [[iterator pattern]]
		- [[chain of responsibility pattern]]
	- #### [[行为变化模式]]
		- [[command pattern]]
		- [[visitor pattern]]
	- #### [[领域问题模式]]
		- [[interpreter pattern]]
- ## [[重构获得模式]]
- ### 什么时候不用模式
	- 代码可读性很差时
	  logseq.order-list-type:: number
	- 需求理解还很浅时
	  logseq.order-list-type:: number
	- 变化没有显现时
	  logseq.order-list-type:: number
	- 不是系统的关键依赖点
	  logseq.order-list-type:: number
	- 项目没有复用价值时
	  logseq.order-list-type:: number
	- 项目将要发布时
	  logseq.order-list-type:: number
- ## 总结
	- 不要为模式而模式
	  logseq.order-list-type:: number
	- 关注抽象类 ＆ 接口
	  logseq.order-list-type:: number
	- 理清[[变化点]]和[[稳定点]]
	  logseq.order-list-type:: number
	- 审视**依赖关系**
	  logseq.order-list-type:: number
	- 要有 Framework 和 Application 的区隔思维
	  logseq.order-list-type:: number
	- 良好的设计是演化的结果
	  logseq.order-list-type:: number