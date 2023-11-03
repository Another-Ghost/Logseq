alias:: trait

- 不同的[[字符集]]，不同的[[表述]]（representation），这给 string 和 I/O 的处理带来变数。例如，对于不同表述，[[end-of-file]]值 或 字符的比较细节，都可能不同。
- [[String]] 和 [[stream]] class 可针对[[内建类型]]而实例化（instantiated），特别是针对 char 和 wchar_t，自C++11 起还加上 char16_t 和 char32_t 。但内建类型的 *接口* 不可改变，因而才会引进一个独立的class，并将**如何处理和表述相关各方面**之细节统统放入该class中，这就是大名鼎鼎的[[trait]] class（特征类）。
- String和stream class都将trait class当作template实参：此实参的默认值是[[char_traits]]并以 string 或 stream 获得的 template 实参（用来定义 字符类型 ）为参数。