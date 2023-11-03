alias:: istream, std::ios/istream

- ``` cpp
  typedef basic_istream<char> istream;
  ```
- # Public 成员函数
	- ## Formatted Input
		- `operator>>`：用于提取[[格式化输入]]。
	- ## Unformatted Input
		- |成员函数名|描述|
		  |--|--|
		  |get|获取[[字符]]|
		  |getline|获取一行数据|