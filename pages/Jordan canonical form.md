alias:: 若尔当标准型, Jordan 标准型

- # Theorem
	- 设 $\cal A$ 是 [[域]]$\mathbb{F}$ 上[[n维线性空间]] $V$ 上的[[线性变换]], 如果 $\cal A$ 的最小多项式 $m(\lambda)$ 在 $F[\lambda]$ 中的[[标准分解式]]为
	  logseq.order-list-type:: number
	  $$
	  m(\lambda)=(\lambda-\lambda_1)^{l_1}(\lambda-\lambda_2)^{l_2}\cdots(\lambda-\lambda_s)^{l_s}.
	  $$
	  那么 $V$ 中存在一个[[基]], 使得 $\cal A$ 在此[[基下的矩阵]] $\boldsymbol{A}$ 为[[Jordan 形矩阵]], 其全部 *主对角元* 是 $\cal A$ 的全部[[特征值]]; 
	  特征值 $\lambda_i$ 在 *主对角线* 上出现的 *次数* 等于 $\lambda$ 的[[代数重数]], 
	  *主对角元* $\lambda_i$ 的[[Jordan 块]]的总数 $N_{j}$ 为
	  $$
	  N_{j}=n-\operatorname{rank}(\mathcal{A}-\lambda_{j}I)
	  $$
	  其中 $t$ *级* [[Jordan 块]] $J_{i}(\lambda_{j})$ 的个数 $N_{j}\left(t\right)$ 为
	  $$
	  N_{j}(t)=\operatorname{rank}(\mathcal{A}-\lambda_{j}I)^{t+1}+\operatorname{rank}(\mathcal{A}-\lambda_{j}I)^{t-1}-2\operatorname{rank}(\mathcal{A}-\lambda_{j}I)^{t}
	  $$
	  $1\leqslant t\leqslant l_{j}, j=1,2,\cdots,s$. 这个 [[Jordan 形矩阵]] $A$称为 $\cal A$ 的[[Jordan 标准形]]; 
	  除去[[Jordan 块]]的 *排列次序* 外, $\cal A$ 的 *Jordan标准形* 是**唯一**的.
		- ## Corollary
			- $\mathbb{F}$ 上 [[n级矩阵]] $\boldsymbol{A}$ [[相似]]于一个[[Jordan 标准型]] $\Longleftrightarrow \boldsymbol{A}$ 的[[最小多项式]] $m(\lambda)$ 或 [[特征多项式]] $f(\lambda)$ 在 $F(\lambda)$ 中可分解成[[一次因式]]的[[乘积]].
			  logseq.order-list-type:: number
			- 设 $\boldsymbol{A}, \boldsymbol{B}\in M_n(F)$, 如果 $\boldsymbol{A}, \boldsymbol{b}$ 都有[[Jordan 标准型]], 那么 $A$ 与 $B$ [[相似]] 
			  logseq.order-list-type:: number
			  $\Longleftrightarrow \boldsymbol{A}$ 与 $\boldsymbol{A}$ 有相同的[[初等因子]].
			  $\Longleftrightarrow$ 有相同的[[Jordan 标准型]](除去[[Jordan 块]]的 *排列次序* 外).
			- 两个 $n$ *级* [[复矩阵]][[相似]] $\Longleftrightarrow$ 它们有相同的[[初等因子]].
			  logseq.order-list-type:: number
-