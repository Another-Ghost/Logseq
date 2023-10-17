# build-In Render Pipeline
	- [[include file]] ，是类似于C++中[[头文件]]的一种文件。在Unity中，它们的文件后缀是 `.cginc` 。
	  使用方法如下：
	  ```
	  CGPROGRAM
	  // ...
	  \#include "UnityCG.cginc"
	  // ...
	  ENDCG
	  ```
	- *CGIncludes文件夹* 在Windows上，它们的位置是：
	  Unity的安装路径/Data/CGIncludes