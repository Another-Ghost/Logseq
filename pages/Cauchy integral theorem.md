public:: true
alias:: 柯西积分定理, 柯西-古萨定理

- # Theorem
	- 设 *函数* $f(z)$ 在[[单连通区域]]$D$内[[解析]]。 $f(z)$ 在 $D$ 内沿任意一条[[简单闭曲线]] $C$ 的[积分]([[复积分]])
	  logseq.order-list-type:: number
	  $$
	  \oint_Cf(z)\mathrm{d}z=0
	  $$
		- ## Corollary
			- 设 $f(z)$ 在[[单连通区域]] $D$ 内[[解析]], $z_0$与 $z_1$ 为 $D$ 内任意两点，$C_1$ 与 $C_{2}$ 为连接 $z_{0}$ 与 $z_{1}$ 的[[积分路线]] $,C_{1},C_{2}$ 都含于 $D$, 则
			  logseq.order-list-type:: number
			  $$
			  \int_{C_{1}}f(z)\mathrm{d}z=\int_{C_{2}}f(z)\mathrm{d}z
			  $$
				- 即当 $f$ 为 $D$ 的[[解析函数]]时[积分]([[复积分]])与[[路线]]无关。
			- 若 $f(z)$ 在[[曲线]]$C$ 围成[[单连通区域]] $D$ 内[[解析]]，则$\oint_Cf(z)\mathrm{d}z=0$。
			  logseq.order-list-type:: number
			- [[Morera定理]]
			  logseq.order-list-type:: number
			  f(z)$在 *单连通区域* $D$内[[连续]]，且$\forall$ *简单闭曲线*[[积分]]为 $0\Longrightarrow$ $f(z)$ 在 $D$ 内[[解析]]。
	- [[复合闭路定理]]
	  logseq.order-list-type:: number
	- 如果 $f(z)$ 是[[单连通区域]] $D$ 内的[[解析]]*函数*,那么由[[变上限的积分]]所确定的 *函数*
	  logseq.order-list-type:: number
	  $$
	  F(z)=\int_{z_0}^zf(\xi)\mathrm{d}\xi 
	  $$
	  也是 $D$ 内的 *解析函数*，而且 $F^{\prime}\left(z\right)=f(z)$.
	- 设 $f(z)$ 在[[单连通区域]] $D$ 内[[解析]]，$F\left(z\right)$ 为 $f(z)$ 的一个[[原函数]],则
	  logseq.order-list-type:: number
	  id:: 64bb814e-7f0e-4dc7-b82c-d0ec3afa70af
	  $$
	  \int_{z_0}^{z_1}f(z)\mathrm{d}z=F(z_1)-F(z_0)
	  $$
	  其中 $z_0,z_1$ 为 $D$ 内的点。
	- [[柯西积分公式]]
	  logseq.order-list-type:: number