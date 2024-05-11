alias:: 可调用对象

- 在C++中，可调用对象（callable object）是指可以像函数那样被调用的任何对象。C++提供了多种方式来实现可调用行为，包括：
- 1. **函数**：最直接的可调用对象就是普通的函数。
- 2. **函数指针**：指向函数的指针，可以被用来间接调用函数。
- ```cpp
   void myFunction(int x) {
       std::cout << "Value: " << x << std::endl;
   }
  - int main() {
       void (*funcPtr)(int) = &myFunction;
       funcPtr(5); // 通过函数指针调用函数
       return 0;
   }
   ```
- 3. **Lambda表达式**：C++11引入的特性，允许定义匿名函数对象。
- ```cpp
   auto lambda = [](int x) { std::cout << "Lambda Value: " << x << std::endl; };
   lambda(10); // 调用Lambda表达式
   ```
- 4. **[[函数对象]]（Functor）**：任何定义了`operator()`的对象，也称为函数对象或仿函数（functor）。
- ```cpp
   struct MyFunctor {
       void operator()(int x) const {
           std::cout << "Functor Value: " << x << std::endl;
       }
   };
  - int main() {
       MyFunctor functor;
       functor(15); // 通过函数对象调用
       return 0;
   }
   ```
- 5. **成员函数指针**：指向类的成员函数的指针，需要实例对象来调用。
- ```cpp
   class MyClass {
   public:
       void myMemberFunction(int x) {
           std::cout << "Member Function Value: " << x << std::endl;
       }
   };
  - int main() {
       MyClass obj;
       void (MyClass::*memberFuncPtr)(int) = &MyClass::myMemberFunction;
       (obj.*memberFuncPtr)(20); // 通过成员函数指针调用
       return 0;
   }
   ```
- 6. **std::function**：C++11中引入的一个模板类，可以用来封装上述所有类型的可调用对象，提供了一种统一的方式来处理可调用对象。
- ```cpp
   #include <functional>
  - int main() {
       std::function<void(int)> func = MyFunctor();
       func(25); // 通过std::function调用函数对象
  - func = myFunction;
       func(30); // 通过std::function调用普通函数
  - func = lambda;
       func(35); // 通过std::function调用Lambda表达式
       return 0;
   }
   ```
- 可调用对象在C++中是一个强大的概念，允许开发者以多种方式封装和传递执行逻辑。