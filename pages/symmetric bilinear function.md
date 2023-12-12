alias:: 对称双线性函数

- # Definition
	- 设[[域]] $\mathbb{F}$ 上[[n维线性空间]] $V$ 上的一个[[双线性函数]], 如果
	  logseq.order-list-type:: number
	  $$
	  f(\alpha,\beta)=f(\beta,\alpha)\:,\quad\forall\:\alpha,\beta\in V
	  $$
	  那么称 $f$ 是[对称]([[symmetric bilinear function]])的;
	- 如果
	  logseq.order-list-type:: number
	  $$
	  f(\alpha,\beta)=-f(\beta,\alpha),\quad\forall\alpha,\beta\in V,
	  $$
	  那么称 $f$ 是[斜对称]([[skew symmetric bilinear function]])的.
- # Theorem
	- 设 $f$ 是[[域]] $\mathbb{F}$ 上[[n维线性空间]] $V$ 上的一个[[双线性函数]], $f$ 在 $V$ 的一个[[基]] $\alpha_{1},\alpha_{2},\cdots,\alpha_n$ 下的[[度量矩阵]]为 $\boldsymbol{A}$, 则
	  logseq.order-list-type:: number
		- $f$ 是[对称]([[symmetric bilinear function]])的
		  logseq.order-list-type:: number
		  $\Longleftrightarrow f(\alpha_i, α_j)=f(\alpha_i,\alpha_j), i,j=1,2,\cdots, n$
		  $\Longleftrightarrow \boldsymbol{A}(i,j)=\boldsymbol{A}(j,i), i,j=1,2,\cdots,n$
		  $\Longleftrightarrow \boldsymbol{A}$ 是[[对称矩阵]].
		- $f$ 是[斜对称]([[skew symmetric bilinear function]])的
		  logseq.order-list-type:: number
		  $\Longleftrightarrow f(\alpha_i, α_j)=-f(\alpha_i,\alpha_j), i,j=1,2,\cdots, n$
		  $\Longleftrightarrow \boldsymbol{A}(i,j)=-\boldsymbol{A}(j,i), i,j=1,2,\cdots,n$
		  $\boldsymbol{A}$ 是[[斜对称矩阵]].
	- 设 $f$ 是[[特征]]不为 $2$ 的 [[域]] $\mathbb{F}$ 上[[n维线性空间]] $V$ 的[[对称双线性函数]]，则 $V$ 中存在一个[[基]], 使得 $f$ 在此 *基* 下的[[度量矩阵]]为[[对角矩阵]].
	  logseq.order-list-type:: number
		- ## Corollary
			- [[特征]]不为 $2$ 的 [[域]] $\mathbb{F}$ 上[[n维矩阵]] $\boldsymbol{A}$ 一定[[合同]]于一个[[对角矩阵]].
			  logseq.order-list-type:: number
	- 设 $f$ 是[[特征]]不为 $2$ 的[[域]] $\mathbb{F}$ 上[[n维线性空间]] $V$ 上的[[斜对称双线性函数]], 则存在 $V$ 的一个[[基]], 把它记成 $\delta_{1},\delta_{-1}, \cdots,\delta_{r},\delta_{-r},\eta_1,cdots,\eta_s$ (其中 $0\leqslant r\leqslant\frac{n}{2},s=n-2r)$, 使得 $f$ 在这个 *基* 下的[[度量矩阵]]具有形式
	  logseq.order-list-type:: number
	  $$
	  \operatorname{diag}\left\{\begin{pmatrix}0&1\\-1&0\end{pmatrix},\cdots,\begin{pmatrix}0&1\\-1&0\end{pmatrix},0,\cdots,0\right\}
	  $$
	  ([[分块对角矩阵]])
-