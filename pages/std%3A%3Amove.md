- ``` C++
  template< class T >
  constexpr std::remove_reference_t<T>&& move( T&& t ) noexcept;
  ```
- `std::move`用于指示对象`t`可能被“移动”，即允许将资源高效地从`t`转移到另一个对象。
  `std::move`产生一个[[xvalue]]表达式，用于标识其参数`t`。
  它与将其`static_cast`为[[右值引用]]类型**完全等效**。
-