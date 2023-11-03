- ``` cpp
  basic_istream& getline( char_type* s, std::streamsize count ); //(1)
  basic_istream& getline( char_type* s, std::streamsize count, char_type delim ); //(2)
  ```
- 从 `*this` 中提取字符，并将它们存储在由 `s` 指向的字符数组的连续位置，直到以下任何一种情况发生（按照所列顺序进行测试）：
	- 在输入序列中出现 文件结束条件 。
	  logseq.order-list-type:: number
	- 下一个可用字符 `c` 是 分隔符，由 `Traits::eq(c, delim)` 决定。分隔符**会被提取**（与 `basic_istream::get()` 不同），并计入 `gcount()`，但**不会被存储**。
	  logseq.order-list-type:: number
	- 已提取 `count - 1` 个字符（`count` 是非正数）。在这种情况下设置[[failbit]]。
	  logseq.order-list-type:: number
-