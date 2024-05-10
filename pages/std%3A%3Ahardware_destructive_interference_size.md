alias:: hardware_destructive_interference_size

- `std::hardware_destructive_interference_size` 是 C++17 引入的一个常量，定义在 `<new>` 头文件中。它用于指示在多线程编程中，两个数据项在内存中应该放置得足够远，以避免伪共享（false sharing）的问题。
- ### 伪共享（ [[False sharing]] ）
	- 在多核处理器上，不同核心之间的缓存是共享的。当多个核心同时访问同一缓存行中的不同数据项时，可能会导致伪共享问题。伪共享会影响程序性能，因为每次一个核心修改了共享的缓存行中的数据，其他核心需要失效自己的缓存行，导致额外的开销。
- ### `std::hardware_destructive_interference_size` 的作用
	- `std::hardware_destructive_interference_size` 可以用来获取系统中处理器缓存行的大小，或者说获取两个数据项在内存中应该放置的最小间隔，以避免伪共享问题。这个值通常是处理器的缓存行大小的整数倍，并且它的设置可能会因处理器架构、操作系统或编译器而异。
	- 使用 `std::hardware_destructive_interference_size` 可以编写更加可移植和高效的多线程代码，以确保共享的数据项在内存中的布局不会导致伪共享问题。
- ### 示例
	- 以下是一个示例，展示了如何使用 `std::hardware_destructive_interference_size`：
	  ```cpp
	  #include <iostream>
	  #include <new>
	  
	  int main() {
	    const std::size_t cache_line_size = std::hardware_destructive_interference_size;
	    std::cout << "Cache line size: " << cache_line_size << " bytes" << std::endl;
	    return 0;
	  }
	  ```
- ### 注意事项
	- `std::hardware_destructive_interference_size` 在某些编译器和平台上可能无法获取到正确的值，或者返回 0。在这种情况下，可以考虑使用一个合适的默认值，或者手动指定缓存行大小。
	- 这个值的大小通常会随着处理器架构、操作系统和编译器的不同而变化，因此在编写可移植的代码时应该格外小心。