alias:: decltype

- 用于检查[[entity]]的[[declared type]]或[[表达式]]的[[type]]和[[value category]]。
- # 解释
	- ```cpp
	      int i = 4;
	      decltype(i) a; //推导结果为int。a的类型为int。
	  ```
-