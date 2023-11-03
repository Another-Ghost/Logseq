alias:: ostream/cout

- ``` cpp
  extern std::ostream cout;
  extern std::wostream wcout;
  ```
- 全局对象 `std::cout` 和 `std::wcout` 控制输出到一个与标准 C 输出[[流]][[stdout]]相关的 implementation-defined type [[流缓冲区]]（派生自[[std::streambuf]]）。
- 这些对象在第一次构造 `std::ios_base::Init` 类型的对象之前或之后被初始化，可用于[[静态]]对象的 构造函数 和 析构函数 的有序初始化（只要在定义对象之前包含了 `<iostream>`）。
- 除非发出 `std::ios_base::sync_with_stdio(false)`，否则可以[安全]([[线程安全]])地从多个线程同时访问这些对象，进行格式化和非格式化的输出。
- 根据[[std::cin]]的规定，`std::cin.tie()` 返回 `&std::cout`。这意味着对 `std::cin` 上的任何输入操作都会执行 `std::cout.flush()`（通过[[basic_istream::sentry]]构造函数执行）。同样，`std::wcin.tie()` 返回 `&std::wcout`。
- 根据 std::cerr 的规定，`std::cerr.tie()` 返回 `&std::cout`。这意味着对 `std::cerr` 上的任何输出操作都会执行 `std::cout.flush()`（通过[[basic_ostream::sentry]]构造函数执行）。同样，`std::wcerr.tie()` 返回 `&std::wcout` 。
- Notes
	- 名称中的 'c' 指的是[[character]]；cout 代表 "character output"，wcout 代表 "[[wide character]] output"。
	- 由于[[模板化变量]]的动态初始化是无序的，因此不能保证在这些变量的初始化开始之前，std::cout 已经被初始化为可用状态，除非构造了[[std::ios_base::Init]]类型的对象。
-