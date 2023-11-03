alias:: std::ios/basic_istream

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
	- 默认会跳过一开始的[[空白字符]]。
-