alias:: operator <<, <<

- ## `std::basic_ostream<CharT,Traits>:: operator<<`
	- ``` cpp
	  basic_ostream& operator<<( bool value );	//(1)	
	  basic_ostream& operator<<( long value );	//(2)	
	  basic_ostream& operator<<( unsigned long value );	//(3)	
	  basic_ostream& operator<<( long long value );	//(4)	(since C++11)
	  basic_ostream& operator<<( unsigned long long value );	//(5)	(since C++11)
	  basic_ostream& operator<<( double value );	//(6)	
	  basic_ostream& operator<<( long double value );	//(7)	
	  basic_ostream& operator<<( const void* value );	//(8)	
	  basic_ostream& operator<<( const volatile void* value );	//(9)	(since C++23)
	  basic_ostream& operator<<( std::nullptr_t );	//(10)	(since C++17)
	  basic_ostream& operator<<( short value );	//(11)	
	  basic_ostream& operator<<( int value );	//(12)	
	  basic_ostream& operator<<( unsigned short value );	//(13)	
	  basic_ostream& operator<<( unsigned int value );	//(14)	
	  basic_ostream& operator<<( float value );	//(15)	
	  basic_ostream& operator<<( /* extended-floating-point-type */ value );	//(16)	(since C++23)
	  basic_ostream& operator<<( std::basic_streambuf<CharT, Traits>* sb );	//(17)	
	  basic_ostream& operator<<( std::ios_base& (*func)(std::ios_base&) );	//(18)	
	  basic_ostream& operator<<(
	  	std::basic_ios<CharT, Traits>& (*func)(std::basic_ios<CharT, Traits>&) );	//(19)	
	  basic_ostream& operator<<(
	      std::basic_ostream<CharT, Traits>& (*func)(std::basic_ostream<CharT, Traits>&) );	//(20)		
	  ```
	-