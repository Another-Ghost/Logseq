alias:: std::ios/basic_istream

- # Public 成员函数
	- ## Formatted Input
		- `operator>>`：用于提取[[格式化输入]]。
	- ## Unformatted Input
		- |成员函数名|描述|
		  |--|--|
		  |[[basic_istream::get]]|提取[[字符]]|
		  |[[basic_istream::getline]]|提取字符，直到找到指定的字符|
		  |[[basic_isteam::read]]|提取字符块|
		  |[[basic_istream::ignore]]|提取并丢弃字符，直到找到指定的字符|
		  |[[basic_istream::peek]]|返回下一个将被读到的字符，但不提取|