- [[basic_istream::sentry]]
- [[basic_ostream::sentry]]
- I/O [[stream]]操作符和函数使用了一种常见的方案，包括预处理、真正的I/O和后处理三个步骤。
  为了实现这个方案，basic_istream 和 basic_ostream 类都定义了一个叫做[[sentry]]的辅助类。sentry类的构造函数负责预处理，析构函数负责后处理。
  因此，在进行格式化或非格式化的I/O操作之前，所有的操作符和函数都会先使用一个sentry对象。
-
- sentry构造函数接受stream strm为实参。预处理和后处理都针对
  strm进行。剩余工作取决于该对象的状态，该状态指示stream是否O
  K，可利用“sentry对象转换为 bool”加以检查。对于input strea
  m，sentry对象构造时可以加上一个选择性的Boolean值，表示是否
  “即使flag skipws设置仍然应该避免跳过空白字符”
-
-