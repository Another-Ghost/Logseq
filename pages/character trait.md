- 不同的[[字符集]]，不同的表述（representation），这给string和I/O的处理带来变数。例如，对于不同表述，end-of-file值或字符的
  比较细节，都可能不同。
- String 和 stream class 可针对内建类型而实例化（instantiat
  ed），特别是针对 char 和wchar_t，自C++11起还加上char16_t和cha
  r32_t。但内建类型的接口不可改变，因而才会引进一个独立的clas
  s，并将“如何处理和表述相关各方面（aspect）”之细节统统放入该
  class中，这就是大名鼎鼎的trait class（特征类）。String和strea
  m class都将trait class当作template实参：此实参的默认值是char_
  traits并以string或stream获得的template实参（用来定义字符类
  型）为参数