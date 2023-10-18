alias:: ELF 可重定位目标文件

- ![image.png](../assets/image_1697608136115_0.png){:height 467/3, :width 466/2}
  上图展示了一个典型的[[ELF 可重定位目标文件]]的格式。
- ## ELF header
  [[ELF header]]以一个 16 字节的序列开始，这个序列描述了生成该文件的系统的[[word size]]和[[字节顺序]]。
  [[ELF]]头剩下的部分包含帮助链接器语法分析和解释目标文件的信息。其中包括[[ELF 头]]的大小、[[目标文件]]的类型（如 可重定位、可执行或者共享的）、 机器类型（如 X86-64)、[[section header table]]的文件偏移，以及[[节头部表]]中[[条目]]的大小和数量。
- ## section header table
  不同[[节]]的位置和大小是由[[节头部表]]描述的，其中[[目标文件]]中每个[[节]]都有一个固定大小的[[条目]]。
- ## Section
  夹在[[ELF 头]]和[[节头部表]]之间的都是[[节]]。一个典型的 [[ELF 可重定位目标文件]]包含下面几个[[节]]：
	- [[.text]]: [[已编译程序]]的[[机器代码]]。
	  logseq.order-list-type:: number
	- [[.rodata]]: [[read-only data]]，比如`printf`语句中的[[format string]]和`switch`语句的[[jump table]]。
	  logseq.order-list-type:: number
	- [[.data]]: 已初始化的全局和静态 C 变量。局部 C 变量在运行时被保存在栈中，既不出
	  logseq.order-list-type:: number
	  现在.data 节中，也不出现在 .bss 节中。
-