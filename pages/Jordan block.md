alias:: Jordan 块, l 级 Jordan block

- # Theorem
	- 设 $\cal A$ 是[[域]] $\mathbb{F}$ 上 $l$ 维[[线性空间]] $W$ 上的[[线性变换]], 如果 $\cal A=kI+B$ , 其中 $\cal B$ 是[[幂零指数]]为 $l$ 的[[幂零变换]]，
	  logseq.order-list-type:: number
	  那么 $W$ 中**存在**一个[[基]]使得 $\cal A$ 在此[[基下的矩阵]] $\boldsymbol A$ 为
	  $$\boldsymbol{A}=\left(\begin{array}{ccccccc}
	  k & 1 & 0 & \cdots & 0 & 0 & 0 \\
	  0 & k & 1 & \cdots & 0 & 0 & 0 \\
	  0 & 0 & k & \cdots & 0 & 0 & 0 \\
	  \vdots & \vdots & \vdots & & \vdots & \vdots & \vdots \\
	  0 & 0 & 0 & \cdots & k & 1 & 0 \\
	  0 & 0 & 0 & \cdots & 0 & k & 1 \\
	  0 & 0 & 0 & \cdots & 0 & 0 & k
	  \end{array}\right)$$
	  把该 *矩阵* 称为一个 [[l 级Jordan 块]], 记作 $\boldsymbol{J}_l(k)$, 其中 $k$ 是[[主对角线]]上的 *元素* ; 
	  > $\boldsymbol{J}_l(k)$ 的[[最小多项式]]是 $(\lambda-k)^{l}$.
	- $\mathbb{F}$ 上 $l$ 级[[矩阵]] $\boldsymbol{A}$ [[相似]]于 $\boldsymbol{J}_l(k)$ $\Longleftrightarrow \boldsymbol{A}$ 的[[最小多项式]]为 $(\lambda-k)^l$.
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number