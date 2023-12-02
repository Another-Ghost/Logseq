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
- $n$位的[[虚拟地址]]包含两个部分：一个 p 位的[[虚拟页面偏移]](VPO)和一个 $(n-p)$ 位的[[虚拟页号]](VPN) 。
  [[MMU]]利用[[VPN]]来选择适当的 PTE。例如， VPN O选择 PTE O, VPN1选择 PTE1,以此类推。将页表条目中物理页号(Physical Page Number, PPN)和虚拟地址中的 VPO串联起来，就得到相应的物理地址。注意，因为物理和虚拟页面都是 P字节的，所以物理页面偏移(Physical Page Offset, PPO)和 VPO是相同的。