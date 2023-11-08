alias:: getline

- ``` cpp
  template< class CharT, class Traits, class Allocator >
  std::istream<CharT, Traits>&
  getline( std::istream<CharT, Traits>&& input, 
  std::string<CharT, Traits, Allocator>& str, CharT delim ); //和istream::getline参数不同，不需要输入count，可以直接通delim结束
  ```
-