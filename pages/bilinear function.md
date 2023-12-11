alias:: 双线性函数

- # Definition
	- 设 $V$ 是[[域]] $\mathbb{F}$ 上的一个[[线性空间]], $V\times V$ 到 $F$ 的一个[[映射]] $f$ 如果满足对于任意 $\alpha, α_1,\alpha_2,β_1,β_2,\beta∈V,k_1,k_2∈F$, 有
	  logseq.order-list-type:: number
	  $$
	  f(k_{1}\alpha_{1}+k_{2}\alpha_{2},\beta)=k_{1}f(\alpha_{1},\beta)+k_{2}f(\alpha_{2},\beta) \tag{1}
	  $$
	  $$
	  f(\alpha,k_{1}\beta_{1}+k_{2}\beta_{2})=k_{1}f(\alpha,\beta_{1})+k_{2}f(\alpha,\beta_{2}) \tag{2}
	  $$
	  那么称 $f$ 是 $V$ 上的一个[[bilinear function]], $f$ 也可写成 $f\left(\alpha,\beta\right)$ .
		- 条件 $(1)$ 表明: 当 $\beta$ 固定时, [[映射]] $α\longmapsto f(\alpha,\beta)$ 是 $V$ 上的一个[[线性函数]], 记作 $\beta_{R}$.
		  logseq.order-list-type:: number
		- 条件 $(2)$ 表明: 当 $α$ 固定时, *映射* $\beta\longmapsto f(\alpha,\beta)$ 是 $V$ 上的一个[[线性函数]], 记作 $\alpha_{L}$.
		  logseq.order-list-type:: number
	- ## 双线性函数的表达式
	  logseq.order-list-type:: number
		- 设 $V$ 是[[域]] $\mathbb{F}$ 上[[n维线性空间]], $V$ 中取一个[[基]] $\alpha_{1},\alpha_{2},\cdots,\alpha_{n}$, 设 $V$ 中[[向量]] $\alpha,\beta$ 在此 *基* 下的[[坐标]]分别为
		  $$
		  \boldsymbol{x}=\left(x_1,x_2,\cdots,x_n\right)^{\prime},\quad \boldsymbol{y}=\left(y_1,y_2,\cdots,y_n\right)^{\prime}
		  $$
		  设 $f$ 是 $V$ 上的一个[[双线性函数]], 则
		  $$
		  f(\alpha,\beta)=f(\sum_{i=1}^{n}x_{i}\alpha_{i},\sum_{j=1}^{n}y_{j}\alpha_{j})=\sum_{i=1}^{n}\sum_{j=1}^{n}x_{i}y_{j}\:f(\alpha_{i},\alpha_{j}) \tag{1}
		  $$
		- 令
		  id:: 64fa6aa7-929c-4e99-9fb2-a00528b6832f
		  $$
		  \boldsymbol{A}=\begin{pmatrix}f(\alpha_1,\alpha_1)&f(\alpha_1,\alpha_2)&\cdots&f(\alpha_1,\alpha_n)\\f(\alpha_2,\alpha_1)&f(\alpha_2,\alpha_2)&\cdots&f(\alpha_2,\alpha_n)\\\vdots&\vdots&&\vdots\\f(\alpha_n,\alpha_1)&f(\alpha_n,\alpha_2)&\cdots&f(\alpha_n,\alpha_n)\end{pmatrix} \tag{2}
		  $$
		  称 $\boldsymbol{A}$ 是[[双线性函数]] $f$ 在 *基* $\alpha_{1},\alpha_2,\cdots, α_n$ 下的[[度量矩阵]],
		  它是由 $f$ 及基 $\alpha_{1},\alpha_{2},\cdots,\alpha_{n}$ 唯一决定的.
		- 从 $(1)$ 式得
		  $$
		  f(\alpha,\beta)=\boldsymbol{x^{\prime}Ay} \tag{3}
		  $$
		  $(3)$ 式和 $(1)$ 式都是[[双线性函数]] $f$ 在 *基* $\alpha_{1},\alpha_{2},\cdots,\alpha_{n}$ 下的[[表达式]].
		- 反之, 任给 $\mathbb{F}$ 上一个[[n级矩阵]] $\boldsymbol{A}=(a_{ij})$ ,定义$V\times V$ 到 $\mathbb{F}$ 的一个[[映射]] $f$ 如下:
		  $$
		  f(\alpha,\beta)=x^{\prime}Ay=\sum_{i=1}^{n}\sum_{j=1}^{n}a_{ij}x_{i}y_{j}
		  \tag{4}$$
		  则 $f$ 是 $V$ 上的一个[[双线性函数]]，且 $f$ 在 *基* $α_1,\alpha_2,\cdots,\alpha_n$ 下的[[度量矩阵]]恰好是 $\boldsymbol{A}$, 这是因为
		  $$
		  f(\alpha_{i},\alpha_{j})=\boldsymbol{\varepsilon}_{i}^{\prime}\boldsymbol{A}\boldsymbol{\varepsilon}_{j}=a_{ij}
		  $$
		  ($\boldsymbol{\varepsilon_i}$ 是除 $i$ [[分量]] 为 $1$, 其余为 $0$ 的 *列向量*)
			- 由于用 $(4)$ 式定义的[[双线性函数]]的[[度量矩阵]]恰好是 $\boldsymbol{A}$, 因此若 $\boldsymbol{x^{\prime}Ay} =\boldsymbol{x^{\prime}By}$，则$\boldsymbol{A}=\boldsymbol{B}$.
		- $(4)$ 式右端的表达式 $\boldsymbol{x^{\prime}Ay}$ 称为 $x_1,x_2, \cdots,x_n$与 $y_{1},y_{2},\cdots, y_n$ 的[[双线性型]].
		- 上述表明: 利用向量 $\alpha,\beta$ 的 *坐标* $x_1,x_2\cdots,x_n$ 与$y_1,y_2,\cdots, y_n$ 的[[双线性型]]可以[[诱导]]出 $V$ 上的一个[[双线性函数]].
- # Theorem
	- 设 $f$ 是 $\mathbb{F}$ 上[[n维线性空间]] $V$ 上的一个[[双线性函数]], $V$ 中取两个[[基]] $a_{1},a_2,\cdots,a_n$ 与 $\beta_1,\beta_2,\cdots,\beta_n$, 设
	  logseq.order-list-type:: number
	  $$
	  (\beta_1,\beta_2,\cdots,\beta_n)=(\alpha_1,\alpha_2,\cdots,\alpha_n)\boldsymbol{P}
	  $$
	  $f$ 在 *基* $\alpha_{1},\alpha_{2},\cdots,\alpha_{n}$ 和 *基* $\beta_{1},\beta_{2},\cdots,\beta_{n}$ 下的[[度量矩阵]]分别为 $\boldsymbol{A},\boldsymbol{B} \Longleftrightarrow$
	  $$
	  \boldsymbol{B}=\boldsymbol{P^{\prime}AP}
	  $$
		- $V$ 上的[[双线性函数]] $f$ 在 $V$ 的不同[[基]]下的[[度量矩阵]]是[[合同]]的.
		  logseq.order-list-type:: number
		- 由 ((c81cc6fd-3935-4693-955f-aaed3d66b5dc)) , 我们把[[双线性函数]] $f$ 在 $V$ 的一个 *基* 下的[[度量矩阵]]的[[秩]]称为 $f$ 的[[矩阵秩]], 记作 $\operatorname{rank_m} f$ .
		  logseq.order-list-type:: number
	- logseq.order-list-type:: number
-
-
-