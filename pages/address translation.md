alias:: 地址翻译, 地址翻译硬件

- |符号|描述|
  |--|--|
  |$N=2^n$|[[虚拟地址空间]]中的地址数量|
  |$M=2^m$|[[物理地址空间]]中的地址数量|
  |$P=2^p$|[[页]]的大小（[[字节]]）|
- 形式上来说，[[地址翻译]]是一个 $N$ 元素的[[虚拟地址空间]](VAS)中的元素和一个 $M$ 元素的[[物理地址空间]](PAS)中元素之间的[[映射]]，
  $$\mathrm{MAP}:\text{VAS}\to\text{PAS}\cup\emptyset$$
  这里
  $$\mathrm{MAP}(A)=\left\{\begin{matrix}A^{\prime}\quad \text{如果虚拟地址 $A$ 处的数据在 PAS 的物理地址 $A^{\prime}$ 处}\\
  \emptyset\quad \text{如果虚拟地址 $A$ 处的数据不在物理内存中}
  \end{matrix}\right.$$
- 下图展示了[[MMU]]如何利用[[页表]]来实现这种 *映射* 。
  ![image.png](../assets/image_1701504528221_0.png)
- [[CPU]]中的一个[[控制寄存器]]，[[页表基址寄存器]](PTBR)指向当前[[页表]]。
- $n$位的[[虚拟地址]]包含两个部分：一个 $p$ 位的[[虚拟页面偏移]](VPO)和一个 $(n-p)$ 位的[[虚拟页号]](VPN) 。
  [[MMU]]利用[[VPN]]来选择适当的[[PTE]]。
  例如， VPN 0 选择 PTE 0 , VPN 1 选择 PTE 1, 以此类推。
- 将[[页表条目]]中[[物理页号]](PPN)和[[虚拟地址]]中的[[VPO]]串联起来，就得到相应的[[物理地址]]。
  注意，因为物理和虚拟页面都是 $P$ 字节的，所以[[物理页面偏移]](PPO)和[[VPO]]是**相同的**。
- 下图展示了当[[页面命中]]时， CPU 硬件执行的步骤。
	- 处理器生成一个[[虚拟地址]]，并把它传送给[[MMU]]。
	  logseq.order-list-type:: number
	- [[MMU]]生成[[PTE]]地址，并从[[高速缓存]]／[[主存]]请求得到它。
	  logseq.order-list-type:: number
	- 高速缓存／主存 向 MMU 返回 PTE。
	  logseq.order-list-type:: number
	- [[MMU]]构造[[物理地址]]，并把它传送给[[高速缓存]]／[[主存]]。
	  logseq.order-list-type:: number
	- [[高速缓存]]／[[主存]]返回所请求的 *数据字* 给[[处理器]]。
	  logseq.order-list-type:: number
	  ![image.png](../assets/image_1701522517597_0.png)