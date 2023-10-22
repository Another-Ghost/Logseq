- ``` C++
  template< class T >
  constexpr std::remove_reference_t<T>&& move( T&& t ) noexcept;
  ```
- `std::move`用于指示对象`t`可能被“移动”，即允许将资源高效地从`t`转移到另一个对象。
  `std::move`产生一个[[xvalue]]表达式，用于标识其参数`t`。
  它与将`t` `static_cast`为[[右值引用]]类型**完全等效**。
- # 解释
- 接受[[右值引用]]参数的函数（包括[[移动构造函数]]、[[移动赋值运算符]]以及诸如`std::vector::push_back`这样的常规成员函数）在使用[[右值]]参数（无论是 [[prvalue]] ，如临时对象，还是将 `std::move` 产生的[[xvalue]]）调用时，通过[[overload resolution]]被选中。
  如果 *参数* 是一个拥有资源的对象，这些重载可以选择但不一定必须移动参数持有的任何资源。例如，[[链表]]的[[移动构造函数]]可能会复制 *链表头* 的指针，并在参数中存储 `nullptr`，而不是分配和复制各个节点。
- 右值引用变量的[[名称]]是左值，并且这个名称必须转换为[[xvalue]]才能绑定到接受右值引用参数的[[函数重载]]，这就是为什么移动构造函数和移动赋值运算符通常使用 `std::move` 的原因：
  id:: 6533a889-fb0b-46f5-9043-b70c9c3e7dd2
- ``` cpp 
  // Simple move constructor
  A(A&& arg) : member(std::move(arg.member)) // the expression "arg.member" is lvalue
  {}
   
  // Simple move assignment operator
  A& operator=(A&& other)
  {
      member = std::move(other.member);
      return *this;
  }
  ```
- 有一个例外情况，当函数参数的类型是类型[[模板参数]]的[[右值引用]]（[[forwarding reference]]或[[universal reference]]）时，此时会使用[[std::forward]]。
- 除非另有规定，**已被移动的**所有标准库对象都被置于一个[[有效但未指定状态]]，这意味着对象的[[class invariants]]成立（因此不带前提条件的函数，例如 *赋值运算符* ，可以在对象**被移动后**安全使用）。
  ``` cpp
  str.back(); // undefined behavior if size() == 0: back() has a precondition !empty()
  if (!str.empty())
  	str.back(); // OK, empty() has no precondition and back() precondition is met
  str.clear(); // OK，OK, clear() has no preconditions
  ```
- 此外，使用[[xvalue]]参数调用的标准库函数可能假定参数是对象的**唯一引用**；如果它是从[[左值]]构造而来的，没有进行别名检查。但是，标准库类型的自我移动赋值保证将对象置于有效（通常是未指定）状态：
  ``` cpp 
  v = std::move(v); //  the value of v is unspecified
  ```
- 这是有关 C++ 中移动语义的重要信息，可以帮助有效利用右值引用和移动操作，从而提高性能和资源管理。
-
- 返回参数 `arg` 的[[右值引用]]。
- 这是一个辅助函数，用于强制在值上使用[[移动语义]]，即使它们具有[[identity]]：直接使用返回的值将导致参数 `t` 被视为[[右值]]。
- 通常，右值是无法通过[[解引用]]获得其地址的值，要么是因为它们是字面值，要么是因为它们是临时的（例如函数返回的值或[[显式构造函数]]调用返回的值）。通过将对象传递给这个函数，可以获得一个引用它的右值。
- 标准库的许多组件实现了移动语义，允许在参数是右值时直接传递对象的资产和属性，而无需复制它们。
- 需要注意的是，在标准库中，移动操作意味着被移动的对象被保留在一个有效但未指定状态。这意味着，在这样的操作之后，被移动的对象的值应该只能被销毁或分配一个新值；否则访问它将产生[[未指定]]的值。
  id:: 6533a284-799f-4eba-af26-ca79f8f5b5f2
-