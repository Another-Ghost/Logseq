- [[stream]]定义了一些类型为[[iostate]]的常量，用以反映[[stream]]的状态。
- [[iostate]]是class [[ios_base]]的一个成员。
- C++ iostate类型的常量表
- |常量|描述|
  |--|--|
  |`std::ios_base::goodbit`|表示流状态正常|
  |`std::ios_base::badbit`| 表示流状态坏，造成不确定的状态|
  |`std::ios_base::failbit`|表示流状态失败|
  |`std::ios_base::eofbit`|表示流已到达文件结尾[[EOF]]|
- [[goodbit]]被定义为0，因此`goodbit`设置意味着其他 bit 均被清为0。
- [[failbit]]和[[badbit]]之间的区别在于后者代表了更严重的错误。
  failbit用于表示在操作过程中出现了错误，但流仍然基本可用。通常情况下，这是由于读取的格式错误，例如尝试读取整数时遇到了一个字母。
  而badbit用于表示流因为未知原因而损坏或丢失数据。例如，将流的位置指向文件起始点之前的位置。
- 需要注意的是，[[eofbit]]常常与[[failbit]]同时发生，因为在到达文件结束后再次尝试读取数据时，会检测到文件结束状态。
  当读取最后一个字符时，eofbit未被设置，但当再次尝试读取字符时，eofbit和failbit都会被设置，因为读取操作失败了。
- ## 可用于 Boolean 表达式 的 stream 操作符
	- [[stream]]类重写了[[operator bool]]和[[operator !]]：
	  |成员函数|描述|
	  |--|--|
	  |`operator bool ()`|stream 是否未出错（相当于 `!fail()` ）|
	  |`operator ! ()`|stream 是否已出错（相当于 `fail()` ）|
	- 用法
	  
	  ``` cpp
	  while(std::cin)
	  {
	      ...
	  }
	  ```
	  此时的 `cin` 被用于[[条件判断]]，于是 `cin` 调用[[operator bool]]
-