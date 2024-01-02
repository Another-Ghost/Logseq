alias:: 统一初始化, uniform initialization

- C++11 引入了一种新的初始化语法，称为统一初始化（Uniform Initialization）。这种语法使用花括号 `{}` 来初始化所有类型的数据。其主要特点和应用如下：
	- **基本类型（Basic Types）**：
	  logseq.order-list-type:: number
	  ```cpp
	     int a{5};  // 整数初始化
	     double b{3.14};  // 浮点数初始化
	     char c{'z'};  // 字符初始化
	  ```
	- **对象和结构体（Objects and Structs）**：
	  logseq.order-list-type:: number
	   假设有一个类 `Point`（点类）：
	   ```cpp
	   class Point {
	   public:
	       int x;
	       int y;
	   };
	  Point p{10, 20};  // 对象初始化
	   ```
	- **数组（Arrays）**：
	  logseq.order-list-type:: number
	   ```cpp
	   int arr[]{1, 2, 3, 4, 5};  // 数组初始化
	   ```
	- **容器类（Container Classes）**（如 `std::vector`）：
	  logseq.order-list-type:: number
	   std::vector<int> v{1, 2, 3, 4, 5};  // 容器初始化
	   ```cpp
	   ```
	- **初始化列表作为函数参数（[[Initializer List]] as Function Arguments）**：
	  logseq.order-list-type:: number
	   ```cpp
	   void foo(std::initializer_list<int> ilist) {
	       // ...
	   }
	  foo({1, 2, 3, 4, 5});  // 使用初始化列表作为函数参数
	   ```
- 统一初始化的好处包括：
	- **减少代码歧义（Reduces Code Ambiguity）**：传统的初始化方式在某些情况下可能产生歧义，而统一初始化减少了这种可能性。
	- **提高代码清晰度（Improves Code Clarity）**：使用统一的语法来初始化所有类型的数据，使得代码更加一致和清晰。
	- **增强类型安全（Enhances Type Safety）**：统一初始化不允许隐式的窄化转换（Narrowing Conversions），这意味着在某些可能导致数据丢失的情况下，编译器会产生错误。