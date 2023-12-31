alias:: 高速缓存存储区, 高速缓存, cache

- 位于处理器芯片上的[[L1 高速缓存]]的容量可以达到数万字节，访问速度几乎和访问寄存器文件一样快。
  一 个容量为数十万到数百万字节的更大的[[L2 高速缓存]]通过一条特殊的总线连接到处理器。进程访问 L2 高速缓存的时间要比访问 Ll 高速缓存的时间长 5 倍，但是这仍然比访问主存的时间快 5~10 倍。
  Ll 和 L2 高速缓存是用一种叫做[[静态随机访问存储器]] (SRAM) 的硬件技术实现的。
  比较新的、处理能力更强大的系统甚至有 三级高速缓存：L1 、L2 和 [[L3]]。
- 系统可以获得一个很大的存储器，同时访问速度也很快，原因是利用了高速缓存的[[局部性]]原理。
-