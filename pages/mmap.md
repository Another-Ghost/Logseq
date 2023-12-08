alias:: mmap 函数

- ## 用户级内存映射
- [[Linux]][[进程]]可以使用[[mmap 函数]]来创建新的[[虚拟内存区域]]，并将[[目标]][映射]([[内存映射]])到这些 区域 中。
- ``` c
  #include <unistd.h>
  #include <sys/mman.h> 
  
  //返回：若成功时则为指向映射区域的指针，若出错则为 MAP_FAILED(-1) 。
  void *mmap(void *start, size_t length, int prot, int flags, int fd, off_t offset);
  ```
- [[mmap]]函数要求[[内核]]创建一个新的[[虚拟内存区域]]，最好是从地址 `start` 开始的一个区域，并将[[文件描述符]] `fd` 指定的 目标 的一个连续的片(chunk)映射到这个新的区域。连续的对象片大小为 leng七 h字节，从距文件开始处偏移量为 offset字节的地方开始。 start地址仅仅是一个暗示，通常被定义为 NULL。为了我们的目的，我们总是假设起始地址为 NULL。图9-32描述了这些参数的意义。