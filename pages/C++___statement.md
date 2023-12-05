alias:: C++/语句

- [[C++/语句]]是[[C++ 程序]]的组成部分，按顺序执行。任何[[函数体]]都是 *[[语句]]序列* 。
- #+BEGIN_PINNED
  ``` cpp
  int main()
  {
      int n = 1;                        // 声明语句
      n = n + 1;                        // 表达式语句
      std::cout << "n = " << n << '\n'; // 表达式语句
      return 0;                         // 返回语句
  }
  ``` 
  #+END_PINNED
- 以下是对您提供的网页链接 [cppreference.com 上的 "Statements" 部分](https://en.cppreference.com/w/cpp/language/statements) 的中文翻译：
- **语句**
  语句是 C++ 程序的组成部分，按顺序执行。任何函数的主体都是一系列语句。例如：
- ```cpp
  int main()
  {
    int n = 1;                        // 声明语句
    n = n + 1;                        // 表达式语句
    std::cout << "n = " << n << '\n'; // 表达式语句
    return 0;                         // 返回语句
  }
  ```
- C++ 包含以下类型的语句：
	- [[labeled statement]]；
	  logseq.order-list-type:: number
	- [[表达式语句]]；
	  logseq.order-list-type:: number
	- [[复合语句]]；
	  logseq.order-list-type:: number
	  id:: 656eec01-3a3b-4a51-9e5e-91a61ca58692
	- [[选择语句]]；
	  logseq.order-list-type:: number
	- [[循环语句]]；
	  logseq.order-list-type:: number
	- [[跳转语句]]；
	  logseq.order-list-type:: number
	- 声明语句；
	  logseq.order-list-type:: number
	- try block；
	  logseq.order-list-type:: number
	  9) 原子和同步块（TM TS）。【57†source】
-