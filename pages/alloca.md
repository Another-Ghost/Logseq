- ``` c
  #include <alloca.h>
  void *alloca(size_t size);
  ```
- `alloca()` 函数在调用者的堆栈帧中分配 size 字节的空间。这个临时空间在调用 `alloca()` 的函数返回给其调用者时会自动释放。