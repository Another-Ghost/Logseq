- ``` cpp
  template< class T >
  constexpr T&& forward( std::remove_reference_t<T>& t ) noexcept;
  
  template< class T >
  constexpr T&& forward( std::remove_reference_t<T>&& t ) noexcept;
  ```
- 1) 将左值按照T的类型转发为左值或右值。
  当T是一个转发引用（即声明为对未加cv限定的函数模板参数的右值引用的函数参数）时，此重载会将参数根据传递给调用函数时的值类别，将其转发给另一个函数。
- 例如，如果在以下包装器中使用，模板会按照以下方式工作：
- ```cpp
  template<class T>
  void wrapper(T&& arg)
  {
    // arg总是左值
    foo(std::forward<T>(arg)); // 根据T将其作为左值或右值进行转发
  }
  ```
- 如果调用`wrapper()`时传递一个右值`std::string`，则`T`被推断为`std::string`（不是`std::string&`、`const std::string&`或`std::string&&`），并且`std::forward`确保将右值引用传递给`foo`。
  如果调用`wrapper()`时传递一个const左值`std::string`，则`T`被推断为`const std::string&`，并且`std::forward`确保将const左值引用传递给`foo`。
  如果调用`wrapper()`时传递一个非const左值`std::string`，则`T`被推断为`std::string&`，并且`std::forward`确保将非const左值引用传递给`foo`。
- 2) 将右值按照右值转发，不允许将右值转发为左值。
  这个重载使得可以按照转发引用参数的原始值类别来转发表达式的结果（例如函数调用），这个表达式可以是右值或左值。
- 例如，如果一个包装器不仅仅是转发其参数，还调用参数的成员函数并转发其结果：
- ```cpp
  // 转换包装器
  template<class T>
  void wrapper(T&& arg)
  {
    foo(forward<decltype(forward<T>(arg).get())>(forward<T>(arg).get()));
  }
  ```
- 其中`arg`的类型可以是：
- ```cpp
  struct Arg
  {
    int i = 1;
    int  get() && { return i; } // 调用这个重载是右值
    int& get() &  { return i; } // 调用这个重载是左值
  };
  ```
- 试图将右值作为左值转发，比如使用左值引用类型T来实例化形式（2），将会导致编译时错误。
- 备注
  有关转发引用的特殊规则（T&&用作函数参数）以及其他详细信息，请参阅模板参数推导和其他转发引用。