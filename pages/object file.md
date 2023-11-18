alias:: 目标文件, object module, 目标模块

- 目标文件有三种形式：
	- [[可重定位目标文件]]
	  logseq.order-list-type:: number
	- [[可执行目标文件]]
	  logseq.order-list-type:: number
	- [[共享目标文件]]
	  logseq.order-list-type:: number
- [[编译器]]和[[汇编器]]生成[[可重定位目标文件]]（包括[[共享目标文件]]）。[[链接器]]生成[[可执行目标文
  件]]。
- 从技术上来说，一个[[目标模块]]就是一个[[字节序列]]，而一个[[目标文件]]就是一个以[[文件]]形式存放在[[磁盘]]中的[[目标模块]]。
- #+BEGIN_TIP
  一般可以互换地使用这些术语。
  #+END_TIP
-
- [[Windows]]使用[[PE]]格式。
  [[Mac OS-X]]使用[[Mach-O]]格式。现代[[x86-64 Linux]]和[[Unix]]系统使用[[ELF]]。