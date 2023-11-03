- [[stream]]定义了一些类型为[[iostate]]的常量，用以反映[[stream]]的状态。
- [[iostate]]是class [[ios_base]]的一个成员。
- C++ iostate类型的常量表
- |常量|描述|
  |--|--|
  |`std::ios_base::goodbit`|表示流状态正常|
  |`std::ios_base::badbit`| 表示流状态坏，造成不确定的状态|
  |`std::ios_base::failbit`|表示流状态失败|
  |`std::ios_base::eofbit`|表示流已到达文件结尾[[EOF]]|
- `goodbit`被定义为0，因此`goodbit`设置意味着其他 bit 均被清为0。
-
- ## 可用于 Boolean 表达式 的 stream 操作符
	- |成员函数|描述|
	  |--|--|
	  |`operator bool ()`|stream 是否未出错（相当于 `!fail()` ）|
	  |||
-