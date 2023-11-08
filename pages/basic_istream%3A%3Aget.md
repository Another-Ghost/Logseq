- ``` cpp
  int_type get();	\\(1)	
  basic_istream& get( char_type& ch );	\\(2)	
  basic_istream& get( char_type* s, std::streamsize count );	\\(3)	
  basic_istream& get( char_type* s, std::streamsize count, char_type delim );	\\(4)	
  basic_istream& get( basic_streambuf& strbuf );	\\(5)	
  basic_istream& get( basic_streambuf& strbuf, char_type delim );	\\(6)
  ```
	- 读取一个[[字符]]并返回（如果可用）。
	  logseq.order-list-type:: number
	  如果无字符可用，则返回 `Traits::eof()` 并设置[[failbit]]和[[eofbit]]。
	- 读取一个字符，如果可用，则存储到 `ch` 中。
	  logseq.order-list-type:: number
	  如果无字符可用，`ch` 不会被修改，同时设置 `failbit` 和 `eofbit`。
	- 读取字符并将它们存储到由 `s` 指向的字符数组中，直到遇到 `'\n'`([[新行]])。
	  logseq.order-list-type:: number
	  最多读取 `std::max(0, count - 1)` 个字符。
	  如果遇到 `'\n'`，它**不会被提取**。
	  > 除`\n`外的其他字符都会被从 stream 中读出来。
-