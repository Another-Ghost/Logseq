alias:: istream/cin, cin

- ``` cpp
  extern std::istream cin;
  extern std::wistream wcin;
  ```
- 全局对象 `std::cin` 和 `std::wcin` 控制来自一个与标准 C 输入[[流]][[stdin]]相关的 implementation-defined type [[流缓冲区]]（派生自 [[std::streambuf]]）的输入。
- 这些对象在第一次构造 `std::ios_base::Init` 类型的对象之前或之后被初始化，可用于[[静态]]对象的 构造函数 和 析构函数 的有序初始化（只要在定义对象之前包含了 <iostream>）。
- 除非使用 `sync_with_stdio(false)`，否则可以[安全]([[线程安全]])地从多个 线程 同时访问这些对象，进行 格式化 和 非格式化 的输入。
- 一旦构造了 `std::cin`，`std::cin.tie()` 返回 `&std::cout`，同样，`std::wcin.tie()` 返回 `&std::wcout`。这意味着 `std::cin` 上的任何[[格式化输入]]操作，如果有待输出的字符，将会强制调用 `std::cout.flush()`。
  id:: 65449bb6-f30d-40a5-8aed-fde717a0376b
- >
- 名称中的 'c' 指的是 "character"（来源自 stroustrup.com FAQ）；cin 代表 "character input"，wcin 代表 "wide character input"。