alias:: 变量模板

- #C++14
- 变量模板定义了[[变量]]或[[静态数据成员]]的家族。
- ## 语法
  ```
  template <parameter-list> variable-declaration
  ```
	- `variable-declaration`：变量的声明，声明的**变量名**成为**模板名**。
	- `parameter-list`：一个非空的模板参数列表，用逗号分隔，每个参数可以是[[非类型参数]]、[[类型参数]]、[[模板参数]]或 其中任何一个的[[参数包]]。
- ## 解释
	- 从[[变量模板]]实例化的变量称为[[实例化变量]]。从[[静态数据成员模板]]实例化的静态数据成员称为 [[实例化静态数据成员]]。
	- #+BEGIN_PINNED
	  变量模板
	  ``` cpp
	  template<class T>
	  constexpr T pi = T(3.1415926535897932385L); // variable template
	   
	  template<class T>
	  T circular_area(T r) // function template
	  {
	      return pi<T> * r * r; // pi<T> is a variable template instantiation
	  }
	  ``` 
	  #+END_PINNED
	- #+BEGIN_PINNED
	  静态数据成员模板
	  ``` cpp
	  using namespace std::literals;
	  struct matrix_constants
	  {
	      template<class T>
	      using pauli = hermitian_matrix<T, 2>; // alias template
	   
	      template<class T> // static data member template
	      static constexpr pauli<T> sigmaX = {{0, 1}, {1, 0}}; 
	   
	      template<class T>
	      static constexpr pauli<T> sigmaY = {{0, -1i}, {1i, 0}};
	   
	      template<class T>
	      static constexpr pauli<T> sigmaZ = {{1, 0}, {0, -1}};
	  };
	  ``` 
	  #+END_PINNED