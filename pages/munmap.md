alias:: munmap 函数

- [[munmap 函数]]用来删除[[虚拟内存的区域]]。
- ``` c
  #include <unistd.h>
  #include<sys/mman.h> 
  
  //返回：若成功则为 0 , 若出错则为 -1
  int munmap(void *start, size_t length);
  ```
- `munmap`函数删除从[[虚拟地址]]`start`开始的，由接下来`length`字节组成的 区域 。接下来对[[已删除区域]]的引用会导致[[段错误]]。