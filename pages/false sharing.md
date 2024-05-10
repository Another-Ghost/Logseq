alias:: 不经意共享, 伪共享

- **False sharing** 是并发编程中一个重要的性能问题，特别是在使用多线程处理数据时。这个问题发生在多个处理器核心尝试访问同一个缓存行（[[cache line]]）上的不同数据时。
- ### 缓存行和 False Sharing
	- 现代计算机处理器使用缓存来提高内存访问速度。缓存通常以缓存行为单位组织，每行通常是 64 字节。处理器在访问内存时会加载整个缓存行到它的本地缓存中。
	- 当多个线程在多核处理器上运行时，如果这些线程操作位于同一缓存行上的不同变量，则可能出现 false sharing。即使这些变量是独立的，每个核心对它所在缓存行的修改也会导致其他核心的缓存行失效，因为其他核心可能也在使用同一缓存行上的其他数据。
- ### False Sharing 的影响
	- False sharing 会导致多个处理器核心频繁地使彼此的缓存失效，这增加了处理器间通信的开销，从而降低了程序的执行效率。这种缓存行竞争可以显著影响多线程程序的性能，特别是在高度优化的计算密集型应用中。
- ### 避免 False Sharing
- 要避免 false sharing，可以采取以下措施：
	- **增加数据对齐和填充**：
	  logseq.order-list-type:: number
	  通过增加数据对齐和填充，确保经常一起使用的数据位于同一个缓存行上，而不相关的数据分布在不同的缓存行上。这可以通过使用 C++11 的 `alignas` 关键字来指定变量或结构体的对齐方式。
	  ```cpp
	  struct alignas(64) PaddedCounter {
	     int value;
	     char padding[60]; // 填充以避免 false sharing
	  };
	  ```
	- **使用缓存行大小的填充**：
	  logseq.order-list-type:: number
	  确保每个核心使用的变量占据一个单独的缓存行，可以通过在共享数据结构中加入足够的填充来实现。
	- **优化数据访问模式**：
	  logseq.order-list-type:: number
	  重新设计数据访问模式，尽量减少不同线程间对同一缓存行的访问。
	- **合理设计数据结构**：
	  logseq.order-list-type:: number
	  在设计并发数据结构时，考虑数据在内存中的布局，避免将频繁被不同线程修改的数据放在同一缓存行内。
	- [[C++17]]标准在头文件 ``<new>`` 中定义了常量 `std::hardware_destructive_interference_size`，用以表示一个字节数的限度，若当前编译目标内数据所在的相邻区域比它小，即有可能造成不经意共享。只要我们令数据的分布范围超出该值，就不会引发不经意共享。
	  logseq.order-list-type:: number
- ### 测试和工具
	- 识别和调试 false sharing 问题通常比较困难，但一些现代的性能分析工具（如 Intel VTune Amplifier, Valgrind 的 Cachegrind 工具等）可以帮助检测代码中可能的 false sharing 问题。
- 总之，false sharing 是多核并行计算中一个重要的性能问题，通过适当的设计和优化，可以显著减少其对程序性能的负面影响。
  <!--Converted by ToLogseq-->