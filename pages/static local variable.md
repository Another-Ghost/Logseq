alias:: 静态局部变量

- # 静态局部变量
  在[[块作用域]]中用[[static]]或[[thread_local]]修饰符声明的变量具有 静态 或 线程存储期，但在第一次[[执行]]到其**声明**时才进行初始化（除非它们的初始化是[[零初始化]]或[[常量初始化]]，这可以在第一次进入 块 之前执行）。在所有后续调用中，将跳过该声明。
  
  如果初始化抛出异常，该变量不被视为已初始化，并且下次控制流经其声明时将再次尝试初始化。
  
  如果初始化递归进入正在初始化该变量的块，行为是未定义的。
  
  如果多个线程同时尝试初始化同一个静态局部变量，则初始化仅发生一次（使用 `std::call_once` 可以获得类似行为）。
  
  注：此功能的通常实现使用双检锁模式的变体，这将已初始化的局部静态变量的运行时开销减少到单个非原子布尔比较。
  
  （自 C++11 起）
  块作用域静态变量的析构函数在程序退出时调用，但前提是初始化成功进行。
  
  同一内联函数（可能隐式内联）的所有定义中的函数局部静态对象都引用在一个翻译单元中定义的同一个对象，只要该函数具有外部链接。
- ### 翻译单元局部实体
  
  C++20 中标准化了翻译单元局部实体的概念，更多细节见相关页面。
  
  一个实体是翻译单元局部（或简称 TU-local）的，如果它：
  
  1. 具有内部链接的名称，或
  2. 没有链接的名称，并且是在 TU-local 实体的定义中引入的，或
  3. 是一个模板或模板特化，其模板参数或模板声明使用了 TU-local 实体。
  
  如果非 TU-local 实体的类型依赖于 TU-local 实体，或者一个非 TU-local 实体的声明或推导指南（自 C++17 起）命名了 TU-local 实体，则通常会发生糟糕的事情（通常违反 ODR）。这些用途在模块接口单元中（除非在其私有模块片段中）或模块分区中被禁止，并在任何其他上下文中被弃用。
  
  在一个翻译单元中出现的声明不能命名在另一个非头文件单元的翻译单元中声明的 TU-local 实体。为模板实例化的声明出现在特化的实例化点。
  
  （自 C++20 起）
- ### 注释
  在顶层命名空间作用域（C 中的文件作用域）中，const 而非 extern 的名称在 C 中具有外部链接，但在 C++ 中具有内部链接。
  
  自 C++11 起，auto 不再是存储类别说明符；它用于表示类型推导。
  
  在 C 中，不能取寄存器变量的地址，但在 C++ 中，声明为 register 的变量在语义上与没有任何存储类别说明符声明的变量无异。
  
  （直到 C++17）
  在 C++ 中，与 C 不同，变量不能声明为 register。
  
  （自 C++17 起）
  具有内部或外部链接的 thread_local 变量的名称在不同作用域中引用时，可能指向相同或不同的实例，这取决于代码是在同一线程还是在不同线程中执行。
  
  extern 关键字还可以用来指定语言链接和显式模板实例化声明，但在这些情况下它不是存储类别说明符（除非声明直接包含在语言链接规范中，在这种情况下，声明
  
  被视为包含 extern 说明符）。
  
  关键字 mutable 在 C++ 语言语法中是存储类别说明符，尽管它不影响存储持续时间或链接。
- ### 本节未完成
  原因：关于在同一翻译单元中重新声明名称的规则。
  除 thread_local 外，存储类别说明符不允许用于显式特化和显式实例化：
  
  ```cpp
  template<class T>
  struct S {
    thread_local static int tlm;
  };
  
  template<>
  thread_local int S<float>::tlm = 0; // 这里不出现 "static"
  ```