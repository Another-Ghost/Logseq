- ``` c
  #include <alloca.h>
  void *alloca(size_t size);
  ```
- `alloca()` 函数在调用者的[[栈帧]]中分配 size 字节的空间。
  这个临时空间在 调用 `alloca()` 的函数 返回给其 调用者 时会自动释放。