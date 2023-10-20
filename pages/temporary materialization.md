#### Temporary materialization
- A [prvalue](https://en.cppreference.com/w/cpp/language/value_category#prvalue) of any complete type `T` can be converted to an xvalue of the same type `T`. This conversion initializes a [temporary object](https://en.cppreference.com/w/cpp/language/lifetime#Temporary_object_lifetime) of type T from the prvalue by evaluating the prvalue with the temporary object as its result object, and produces an xvalue denoting the temporary object. If `T` is a class or array of class type, it must have an accessible and non-deleted destructor.
- ```
  struct S { int m; };
  int i = S().m; // member access expects glvalue as of C++17;
               // S() prvalue is converted to xvalue
  ```
- Temporary materialization occurs in the following situations:
- when [binding a reference](https://en.cppreference.com/w/cpp/language/reference_initialization) to a prvalue;
- when performing a [member access](https://en.cppreference.com/w/cpp/language/operator_member_access) on a class prvalue;
- when performing an array-to-pointer conversion (see above) or [subscripting](https://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_subscript_operator) on an array prvalue;
- when initializing an object of type std::initializer_list<T> from a [braced-init-list](https://en.cppreference.com/w/cpp/language/list_initialization);
- when [`typeid`](https://en.cppreference.com/w/cpp/language/typeid) is applied to a prvalue (this is part of an unevaluated expression);
- when [`sizeof`](https://en.cppreference.com/w/cpp/language/sizeof) is applied to a prvalue (this is part of an unevaluated expression);
- when a prvalue appears as a [discarded-value expression](https://en.cppreference.com/w/cpp/language/expressions#Discarded-value_expressions).
- Note that temporary materialization does *not* occur when initializing an object from a prvalue of the same type (by [direct-initialization](https://en.cppreference.com/w/cpp/language/direct_initialization) or [copy-initialization](https://en.cppreference.com/w/cpp/language/copy_initialization)): such object is initialized directly from the initializer. This ensures "guaranteed copy elision".