alias:: operator >>, >>

- ## `std::basic_istream<CharT,Traits>:: operator>>`
	- ``` cpp
	  basic_istream& operator>>( unsigned short& value );
	  (1)	
	  basic_istream& operator>>( unsigned int& value );
	  (2)	
	  basic_istream& operator>>( long& value );
	  (3)	
	  basic_istream& operator>>( unsigned long& value );
	  (4)	
	  basic_istream& operator>>( long long& value );
	  (5)	(since C++11)
	  basic_istream& operator>>( unsigned long long& value );
	  (6)	(since C++11)
	  basic_istream& operator>>( float& value );
	  (7)	
	  basic_istream& operator>>( double& value );
	  (8)	
	  basic_istream& operator>>( long double& value );
	  (9)	
	  basic_istream& operator>>( bool& value );
	  (10)	
	  basic_istream& operator>>( void*& value );
	  (11)	
	  basic_istream& operator>>( short& value );
	  (12)	
	  basic_istream& operator>>( int& value );
	  (13)	
	  basic_istream& operator>>( /* extended-floating-point-type */& value );
	  (14)	(since C++23)
	  basic_istream& operator>>( std::ios_base& (*func)(std::ios_base&) );
	  (15)	
	  basic_istream& operator>>( std::basic_ios<CharT, Traits>&
	                                 (*func)(std::basic_ios<CharT, Traits>&) );
	  (16)	
	  basic_istream& operator>>( basic_istream& (*func)(basic_istream&) );
	  (17)	
	  basic_istream& operator>>( std::basic_streambuf<CharT, Traits>* sb );
	  (18)	
	  ```
	- 经由 `>>` 读入一个 `char` 或 `wchar_t` 字符时，默认会跳过开头的[[空白字符]]。如果你想读入所有字符（包括空白字符），可清除 `skipws` flag或利用成员函数[[basic_istream::get]]。
	- [[C-string]]（亦即 `char*` ）只读入真正的文字，因此默认情况下读得的开头[[空白字符]]均会跳过，一直读到另一个[[空白字符]]或[[end-of-file]]为止。是否跳过起头的空白字符同样可由flag `skipws` 控制。