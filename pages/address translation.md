alias:: 地址翻译, 地址翻译硬件

- |符号|描述|
  |--|--|
  |$N=2^n$|[[虚拟地址空间]]中的地址数量|
  |$M=2^m$|[[物理地址空间]]中的地址数量|
  |$P=2^p$|[[页]]的大小（[[字节]]）|
- 形式上来说，地址翻译是一个 $N$ 元素的[[虚拟地址空间]](VAS)中的元素和一个 $M$ 元素的[[物理地址空间]](PAS)中元素之间的[[映射]]，
  $$\mathrm{MAP}:\text{VAS}\to\text{PAS}\cup\emptyset$$
  这里
  $$\mathrm{MAP}(A)=\left\{\begin{matrix}A^{\prime}\quad \text{如果虚拟地址 $A$ 处的数据在 PAS 的物理地址 $A^{\prime}$ 处}\\
  \emptyset\quad \text{如果虚拟地址 $A$ 处的数据不在物理内存中}
  \end{matrix}\right.$$
-