alias:: mmap 函数

- ## 用户级内存映射
- [[Linux]][[进程]]可以使用[[mmap 函数]]来创建新的[[虚拟内存区域]]，并将[[目标]][映射]([[内存映射]])到这些 区域 中。
- ``` c
  #include <unistd.h>
  #include <sys/mman.h> 
  
  //返回：若成功时则为指向映射区域的指针，若出错则为 MAP_FAILED(-1) 。
  void *mmap(void *start, size_t length, int prot, int flags, int fd, off_t offset);
  ```