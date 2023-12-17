alias:: 动态内存分配器, 分配器, 内存分配器

- [[动态内存分配器]]是一个[[应用级程序]]。它**维护**着一个进程的[[虚拟内存区域]]，称为[[堆]]。
	- 系统之间细节不同，但是不失通用性，假设 堆 是一个[[请求二进制零的区域]]，它紧接在[[未初始化的数据区域]]后开始，并向上生长（向**更高的**地址）。
	- 对于每个 进程 ，[[内核]]维护着一个变量[[brk]](读做"break"),它指向 堆的顶部 。
	- ![image.png](../assets/image_1702064189044_0.png)
- [[分配器]]将堆视为一组不同大小的[[块]]的集合来维护。
  每个[[块]]就是一个连续的[[虚拟内存片]], 要么是[[已分配块]]，要么是[[空闲块]]。
	- [[已分配块]]显式地保留为供[[应用程序]]使用。
	- [[空闲块]]可用来分配。空闲块保持空闲，直到它显式地被应用所[[分配]]。
- 一个[[已分配的块]]保持已分配状态，直到它被[[释放]]，这种释放要么是[[应用程序]] *显式执行* 的，要么是[[内存分配器]]自身 *隐式执行* 的。
- 分配器有两种基本风格。两种风格都要求应用 *显式地* 分配块。它们的不同之处在于由哪个[[实体]]来负责[[释放]]已分配的块。
	- [[显式分配器]]
		- 要求应用 *显式地释放* 任何已分配的块。
		- 例如，C标准库 提供一种叫做[[malloc 程序包]]的[[显式分配器]]。 C程序通过调用[[malloc]]函数来．分配一个块，并通过调用[[free]]函数来释放一个块。 C++中的`new`和`delete`操作符与 C中的`malloc`和`free`相当。
	- [[隐式分配器]]
		- 要求[[分配器]]检测一个[[已分配块]]何时不再被程序所使用，那么就释放这个块。隐式分配器也叫做[[垃圾收集器]](garbage collector), 而自动释放 *未使用的已分配的块* 的过程叫做[[垃圾收集]](garbage collection)。
		- 例如，诸如 Lisp、 ML 以及 Java 之类的高级语言就依赖垃圾收集来释放已分配的块。
- # 分配器的要求
	- [[显式分配器]]必须在一些相当严格的约束条件下工作：
		- 处理任意请求序列。
		  logseq.order-list-type:: number
			- 一个应用可以有任意的分配请求和释放请求序列，只要满足约束条件：每个释放请求必须对应于一个当前已分配块，这个块是由一个以前的分配请求获得的。因此，分配器不可以假设分配和释放请求的顺序。例如，分配器不能假设所有的分配请求都有相匹配的释放请求，或者有相匹配的分配和空闲请求是嵌套的。
		- 立即响应请求。
		  logseq.order-list-type:: number
			- 分配器必须立即响应分配请求。因此，**不允许**分配器为了提高性能**重新排列**或者**缓冲请求**。
		- 只使用堆。为了使分配器是可扩展的，分配器使用的任何非标量数据结构都必须保存在堆里。
		  logseq.order-list-type:: number
		- 对齐块（对齐要求）。分配器必须对齐块，使得它们可以保存任何类型的数据对象。
		  logseq.order-list-type:: number
		- 不修改已分配的块。分配器只能操作或者改变空闲块。特别是，一旦块被分配了，就不允许修改或者移动它了。因此，诸如压缩已分配块这样的技术是不允许使用的。
		  logseq.order-list-type:: number
- # 分配器的目的
	- 在这些限制条件下，分配器的编写者试图实现吞吐率最大化和内存使用率最大化，而这两个性能目标通常是相互冲突的。
		- 最大化[[吞吐率]]。假定 n个分配和释放 请 求的某种序列：
		  logseq.order-list-type:: number
		  $$
		  R_0,R_1,\cdots,R_k,\cdots,R_{n-1}
		  $$
		  我们希望一个分配器的吞吐率最大化，吞吐率定义为每个单位时间里完成的请求数。例如，如果一个分配器在 1 秒内完成 500 个分配请求和 500 个释放请求，那么它的吞吐率就是每秒 1000 次操作。一般而言，我们可以通过使满足分配和释放请求的平均时间最小化来使吞吐率最大化。正如我们会看到的，开发一个具有合理性能的分配器并不困难，所谓合理性能是指一个分配请求的最糟运行时间与空闲块的数扯成线性关系，而一个释放请求的运行时间是个常数。
		- 最大化[[内存利用率]]。天真的程序员经常不正确地假设虚拟内存是一个无限的资源。实际上，一个系统中被所有进程分配的虚拟内存的全部数量是受磁盘上交换空间的数最限制的。好的程序员知道虚拟内存是一个有限的空间，必须高效地使用。对千可能被要求分配和释放大块内存的动态内存分配器来说，尤其如此。
		  logseq.order-list-type:: number
	- 有很多方式来描述一个分配器使用堆的效率如何。在我们的经验中，最有用的标准是[[峰值利用率]] (peak utilization) 。像以前一样，我们给定 n 个分配和释放请求的某种顺序 R 。 , R1, …, Rk' …, Rn - I如果一个应用程序请求一个 p 字节的块，那么得到的已分配块的[[有效载荷]] (payload) 是 p字节。在请求凡完成之后，[[聚集有效载荷]] (aggregate payload) 表示为 pk' 为当前已分配的块的有效载荷之和，而 Hk 表示堆的当前的（单调非递减的）大小。那么，前 k+l 个请求的峰值利用率，表示为 Uk' 可以通过下式得到： 
	  id:: 65744840-c291-42d4-94df-5a46f7ca8453
	  $$
	  U_k=\frac{\max_{i\le k}P_i}{H_k}
	  $$
	  那么，分配器的目标就是在整个序列中使峰值利用率 U.-1 最大化。正如我们将要看到的，在最大化吞吐率和最大化利用率之间是互相牵制的。特别是，以堆利用率为代价，很容易编写出吞吐率最大化的分配器。分配器设计中一个有趣的挑战就是在两个目标之间找到一个适当的平衡。
	- #+BEGIN_PINNED
	  我们可以通过让 H k 成为前 k+l 个请求的最高峰，从而使得在我们对队的定义中放宽单调非递减的假设，并且允许堆增长和降低 。
	  #+END_PINNED
- # 实现中要考虑的问题
	- 一个实际的分配器要在[[吞吐率]]和[[内存利用率]]之间把握好平衡，就必须考虑以下几个问题：
		- [[空闲块组织]] ：我们如何 *记录* 空闲块？
		- [[放置已分配块]]：我们如何选择一个合适的空闲块来放置一个新分配的块？
		- [[分割空闲块]]：在将一个新分配的块放置到某个空闲块之后，我们如何处理这个空闲块中的 *剩余部分* ？
		- [[合并空闲块]]：我们如何处理一个刚刚被[[释放]]的块？
-