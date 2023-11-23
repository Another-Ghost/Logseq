alias:: 线性空间, 向量空间

- # Definition
	- 设 $V$ 是一个 *非空*[[set]]，$F$ 是一个[[field]]。
	- 如果$V$上有一个[[运算]]（即$V\times V$到$V$的一个[[映射]]），称为[[加法]]，即$(\alpha, \beta)\longmapsto\gamma$，把$\gamma$称为$\alpha$与$\beta$的[[和]]，记作$\alpha+\beta=\gamma$；
	- $F$与$V$有一个[[运算]]（即$F\times V$到$V$的一个映射），称为[[纯量乘法]]，即$(k, \alpha)\longmapsto\delta$，把$\delta$称为$k$与$\alpha$的[[纯量乘积]]，记作$k\alpha=\delta$；
	- 并且对于$\forall\alpha,\beta,\gamma\in V$，$\forall k,l\in F$，满足下述8条运算法则：
		- $\alpha+\beta=\beta+\alpha$ （[[加法交换律]]）;
		  logseq.order-list-type:: number
		- $(\alpha+\beta)+\gamma=\alpha+(\beta+\gamma)$ （[[加法结合律]]）;
		  logseq.order-list-type:: number
		- $V$中有一个 *元素*，记作 $0$，它使得具有
		  logseq.order-list-type:: number
		  $$\alpha+0=\alpha,\quad \forall\alpha\in V$$
			- 性质的 *元素* $0$ 称为$V$的[[零元]]；
		- 对于$\alpha\in V$，存在$\beta\in V$，使得
		  logseq.order-list-type:: number
		  $$\alpha+\beta=0$$
			- 具有该性质的元素$\beta$称为$\alpha$的[[负元]]；
		- $1\alpha=\alpha$，其中 $1$ 是 $F$ 的[[单位元]]；
		  logseq.order-list-type:: number
		- $(kl)\alpha=k(l\alpha)$;
		  logseq.order-list-type:: number
		- $(k+l)\alpha=k\alpha+l\alpha$; 
		  logseq.order-list-type:: number
		- $k(\alpha+\beta)=k\alpha+k\beta$，
		  logseq.order-list-type:: number
	- 那么称$V$是域$F$上的一个[[线性空间]]。
	- 把 $V$ 中 *元素* 称为一个[[向量]]。
- # Theorem
	- 设$V$是 *域* $F$上的一个线性空间，$\forall\alpha\in V$，$\forall k\in F$具有如下性质：$
	  logseq.order-list-type:: number
		- V$的[[零元]]唯一。
		  logseq.order-list-type:: number
		- $\forall\alpha\in V$的[[负元]]唯一。
		  logseq.order-list-type:: number
		- $0\alpha=0$。
		  logseq.order-list-type:: number
		- $k0=0$。
		  logseq.order-list-type:: number
		- 如果$k\alpha=0$，那么$k=0$或$\alpha=0$。
		  logseq.order-list-type:: number
		- $(-1)\alpha=-\alpha$ 。
		  logseq.order-list-type:: number
-
-
- # 向量集的线性相关与线性无关
	- |研究的对象|[[线性相关]]|[[线性无关]]|
	  |--|--|--|
	  |向量组$\alpha_1,\cdots,\alpha_s(s\ge 1)$|$F$中有不全为$0$的元素$k_1,\cdots k_s$，使得$k_1\alpha_1+\cdots+k_s\alpha_s=0$|从$k_1\alpha_1+\cdots+k_s\alpha_s=0$可以推出$k_1=\cdots=k_s=0$|
	  |$V$的非空有限子集|给这个子集的元素一种**编号**所得的**向量组**线性相关|给这个子集的元素一种**编号**所得的**向量组**线性无关|
	  |$V$的无限子集$W$|$W$有一个**有限子集**线性相关|$W$的任一**有限子集**都线性无关|
-
- # 研究线性空间的途径
	- 1. [[基]]
	  2. [[直和]][[子空间]]
	  3. [[同构]]
	  4. [[商集]]
-