alias:: 迭代法的收敛性, 迭代法收敛

- ### [[矩阵序列的收敛性]]
- ## Definition
	- 设有方程组
	  logseq.order-list-type:: number
	  $$\boldsymbol {x}=\boldsymbol{B}\boldsymbol {x}+\boldsymbol{F}$$
	  对于任意[[初始向量]]$\boldsymbol x^{(0)}$及任意$\boldsymbol F$，如果 $\lim_{k\to\infty}x^{(k)}$([[极限]])**存在**，称此[[迭代法收敛]]，显然 $x^{*}$ 就是此[[线性方程组的解]]，否则称此[[迭代法发散]].
		- 由上述讨论,需要研究 $\left\{\boldsymbol x^{(k)}\right\}$ 的[[收敛性]]. 引进[[误差向量]]
		  $$
		  \bold{\varepsilon}^{(k+1)}=\boldsymbol{x}^{(k+1)}-\boldsymbol x^*
		  $$
		  易得
		  $$
		  \boldsymbol{\varepsilon}^{(k+1)}=\boldsymbol{B}\boldsymbol{\varepsilon}^{(k)}(k=0,1,2,\cdots)
		  $$
		  递推得
		  $$
		  \boldsymbol{\varepsilon}^{(k)}=\boldsymbol{B\varepsilon}^{(k-1)}=\cdots=\boldsymbol{B^k\varepsilon}^{(0)}
		  $$
		  要考察 $\{\boldsymbol x^{(k)}\}$ 的[[收敛性]]，就要研究 $\boldsymbol B$ 在什么条件下有 $\lim_{k\to\infty}\boldsymbol{\varepsilon}^{(k)}=\boldsymbol{0}$, 亦即要研究 $\boldsymbol B$ 满足什么条件时有 $\lim_{k\to\infty}\boldsymbol B^{k}→\boldsymbol 0$ ([[零矩阵]]) .
- ## Theorem
	- ### [[迭代法基本定理]]
	  logseq.order-list-type:: number
	  设有方程组
	  $$\boldsymbol {x}=\boldsymbol{B}\boldsymbol {x}+\boldsymbol{F}$$
	  对于任意[[初始向量]]$\boldsymbol x^{(0)}$及任意$\boldsymbol F$, 解此方程组的迭代法（即$\boldsymbol x^{(k+1)}=\boldsymbol B\boldsymbol x^{(k)}+\boldsymbol F$）[收敛]([[迭代法收敛]])的充要条件是 $\rho(\boldsymbol B)<1$ ，其中 $\rho(\boldsymbol B)$ 为 $\boldsymbol B$ 的[[谱半径]].
		- 称 $R(\boldsymbol B)=-\ln\rho(\boldsymbol B)$ 为迭代法的[[收敛速度]]。
	- ### 迭代法收敛的充分条件
	  logseq.order-list-type:: number
		- 如果方程组 $\boldsymbol x=\boldsymbol{Bx}+\boldsymbol F$ 的迭代公式为$\boldsymbol x^{(k+1)}=\boldsymbol{Bx}^{(k)}+\boldsymbol F$,且迭代矩阵的某一种范数$\|\boldsymbol B\|_p=q<1$,则有
		  logseq.order-list-type:: number
			- 迭代法收敛，即对任取 $\boldsymbol x^{(\mathrm{0})}$, 有$\lim_{k\to\infty} \boldsymbol x^{(k)}=\boldsymbol x^*$, 且 $\boldsymbol x^*=\boldsymbol {Bx}^*+\boldsymbol F;$
			  logseq.order-list-type:: number
			- logseq.order-list-type:: number
			  $$\parallel\boldsymbol  x^*-\boldsymbol x^{(k)}\parallel_p\leqslant\frac q{1-q}\parallel \boldsymbol x^{(k)}-\boldsymbol x^{(k-1)}\parallel_p ;$$
			- logseq.order-list-type:: number
			  $$\parallel \boldsymbol x^{*}-\boldsymbol x^{(k)}\parallel_p\leqslant\frac{q^{k}}{1-q}\parallel \boldsymbol x^{(1)}-\boldsymbol x^{(0)}\parallel_p.$$
		- 如果 $\boldsymbol A\in\mathbb{R}^{n\times n}$ 为[[严格对角优势矩阵]]或为 [[不可约]][[弱对角优势矩阵]]，则对任意的 $\boldsymbol x^{(\mathrm{0})}$, 解方程组 $\boldsymbol{Ax}=\boldsymbol b$ 的 [[Jacobi 迭代法]]，[[Gauss-Seidel 迭代法]]均收敛.
		  logseq.order-list-type:: number
		-