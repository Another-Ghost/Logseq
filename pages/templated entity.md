<<<<<<< HEAD
alias:: 模板化实体, temploid, templated, 模板化

- [[模板化实体]]是在[[模板定义]]中定义的（或对于[[lambda 表达式]]来说，创建的）任何[[实体]]。
  id:: 656dfb3a-e215-424c-82fa-d3777cbcf9dd
  以下都是模板化实体：
	- [[类模板]]/[[函数模板]]/[[变量模板]]
	- [[concept]]
	- 模板实体 的[[成员]]（如类模板的非模板成员函数）
	- [[枚举值]]，如果[[枚举]]是 模板化实体 。
	- 在 模板化实体 内定义或创建的任何实体：[[局部类]]、[[局部变量]]、[[友元函数]]等 。
	- 在 模板化实体 的声明中出现的[[lambda 表达式]]的[[闭包类型]]。
- #+BEGIN_PINNED
  例如，在下面的代
  ``` cpp
  template<typename T>
  struct A
  {
    void f() {}
  };
  id f() {}
    };
    ```
  `A::f` 函数不是[[函数模板]]，但仍然被认为是 *模板化* 的。
  #+END_PINNED
	- [[templated function]]是指[[函数模板]]或 *被[[模板化]]的函数* 。
	- [[templated class]]是指[[类模板]]或 *被模板化的类* 。
	- [[templated variable]]是指[[变量模板]]或 *被模板化的变量* 。
=======
alias:: 模板实体, temploid
>>>>>>> 81614d5fbdd137895c185ced7ef1bbfd3a4979bc
