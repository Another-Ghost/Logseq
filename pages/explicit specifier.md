alias:: explicit

- 在函数调用时，C++允许每个参数进行一次隐式转换。对于类，这可能会带来一些问题，因为这并不总是预期的行为。例如，如果我们在[示例](logseq://graph/Logseq?block-id=653280eb-8e9c-4d9e-a740-511017191a15)中添加以下函数：
- ``` cpp 
  void fn(B arg) {}
  ```
- 这个函数接受类型为 B 的参数，但实际上也可以使用类型为 A 的对象作为参数来调用：
- ```cpp
  fn(foo);
  ```
- 这可能不是预期的行为，但无论如何，可以通过在受影响的[[构造函数]]前加上`explicit`关键字来阻止这种[[隐式转换]]发生：
- ```cpp
  class B {
  public:
    explicit B(const A& x) {}
    B& operator=(const A& x) { return *this; }
    operator A() { return A(); }
  };
  
  void fn (B x) {}
  
  int main ()
  {
    A foo;
    B bar (foo);
    bar = foo;
    foo = bar;
    
  //  fn (foo);  // not allowed for explicit ctor.
    fn (bar);  
  
    return 0;
  }
  
  ```
- 此外，使用`explicit`标记的[[构造函数]]不能使用[[赋值]]样式的语法进行调用；在上述示例中，`bar`不能通过以下方式构造：
- ```cpp
  B bar = foo;
  ```
- [[type-cast 成员函数]] 也可以标记为`explicit`。这将以与目标类型的`explicit`构造函数相同的方式阻止[[隐式转换]]。