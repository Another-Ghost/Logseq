alias:: 虚继承

- 为了解决多继承时的命名冲突和冗余数据问题，C++ 提出了虚继承，使得在派生类中只保留一份间接基类的成员。
- 在继承方式前面加上 virtual关键字就是虚继承，请看下面的例子：
  ``` cpp
  //间接基类A
  class A{
  protected:
    int m_a;
  };
  - //直接基类B
  class B: virtual public A{  //虚继承
  protected:
    int m_b;
  };
  - //直接基类C
  class C: virtual public A{  //虚继承
  protected:
    int m_c;
  };
  - //派生类D
  class D: public B, public C{
  public:
    void seta(int a){ m_a = a; }  //正确
    void setb(int b){ m_b = b; }  //正确
    void setc(int c){ m_c = c; }  //正确
    void setd(int d){ m_d = d; }  //正确
  private:
    int m_d;
  };
  - int main(){
    D d;
    return 0;
  }
  ```
- [[virtual public]]
- [[virtual protected]]
- [[virtual private]]