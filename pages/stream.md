alias:: 流

- 基本的[[stream]]类层次体系：
  ![image.png](../assets/image_1699006529668_0.png){:height 344, :width 566}
- ## 全局性的 stream 对象
	- [[IOStream]]程序库定义了数个[[全局]]性的 stream 对象。
	  它们分别以`char`或对应的`wchar_t`作为字符类型，用来访问标准I/O通道。见下表：
	- |名称|类型|用途|
	  |--|--|--|
	  |[[cin]]|istream|从[[标准 input 通道]]读取数据|
	  |[[cout]]|ostream|将一般数据写至[[标准 error 通道]]|
	  |[[cerr]]|ostream|将[[报错信息]]写至[[标准 error 通道]]|
	  |[[clog]]|ostream|将[[日志信息]]写至[[标准 logging 通道]]|
	- 每一个都有相对应的[[宽字符]]版本，依次为 `wcin`，`wcout`，`cerr`，`clog`。