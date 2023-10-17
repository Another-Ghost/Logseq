alias:: 核, Ker

- # Definition
	- 设 $\mathcal{A}$ 是[[域]] $F$ 上的[[线性空间]] $V$ 到 $V'$ 的一个[[线性映射]], $V^{\prime}$ 的[[零向量]]在 $\mathcal{A}$ 下的[[原像集]]称为 $A$ 的[[核]], 记作 $\operatorname{Ker} A$. 即
	  logseq.order-list-type:: number
	  $$
	  \operatorname{Ker}\mathcal{A}:=\{\alpha\in V\mid\mathcal{A}{\alpha}=0^{\prime}\} 
	  $$
	- $\mathcal{A}$ 的[[像]]记作 $\operatorname{Im} \mathcal{A}$ 或 $\mathcal{A}V$.
	  logseq.order-list-type:: number
- # Theorem
	- 设 $\mathcal{A}$ 是[[域]] $F$ 上[[线性空间]] $V$ 到 $V^{\prime}$ 的一个[[线性映射]], 则 $\operatorname{Ker}\mathcal{A}$ 是 $V$ 的一个[[子空间]];
	  logseq.order-list-type:: number
	  $\operatorname{Im} A$([[像]]) 是 $V^{\prime}$ 的一个[[子空间]].
	- 设 $\mathcal{A}$ 是[[域]] $F$ 上[[线性空间]] $V$ 到 $V'$ 的一个[[线性映射]], 则
	  logseq.order-list-type:: number
		- $\mathcal{A}$ 是[[单射]]$\Longleftrightarrow \operatorname{Ker}\mathcal{A}=0$([[核]]);
		  logseq.order-list-type:: number
		- $\cal{A}$ 是[[满射]]$\Longleftrightarrow \operatorname{Im}\mathcal{A}=V^{\prime}$([[像]]).
		  logseq.order-list-type:: number
	- 设 $A$ 是[[域]] $F$ 上[[线性空间]] $V$ 到$V'$ 的一个[[线性映射]],令
	  logseq.order-list-type:: number
	  \begin{aligned}
	  \sigma:\quad V/\operatorname{Ker}\mathcal{A}&\longrightarrow\operatorname{Im}\mathcal{A}\\
	  \alpha+\operatorname{Ker}\mathcal{A}&\longmapsto\mathcal{A}\alpha
	  \end{aligned}
	  则 $\sigma$ 是 $V/\operatorname{Ker}\mathcal{A}$([[核]]) 到 $\operatorname{Im}\cal{A}$([[像]])的一个[[同构映射]]，从而
	  $$
	  V/\mathrm{Ker~}\mathcal{A}\cong\mathrm{Im~}\mathcal{A}
	  $$
	- 设 $V$ 和 $V'$ 都是[[域]] $F$ 上的[[线性空间]], 且 $V$ 是[[有限维]]的。设 $\mathcal{A}$ 是 $V$ 到 $V^{\prime}$ 的一个[[线性映射]], 
	  logseq.order-list-type:: number
	  则 $\operatorname{Ker}\cal{A}$和 $\operatorname{Im}\cal{A}$ 都是[[有限维]]的, 且
	  $$
	  \dim(\mathrm{Ker~}\mathcal{A})+\dim(\mathrm{Im~}\mathcal{A})=\dim(V)
	  $$
		- 当 $V$ 是[[有限维]]时, $V$ 到 $V^{\prime}$ 的[[线性映射]]$\cal{A}$的[[核]]的[[维数]]也称为$\cal{A}$的[[零度]]; 
		  $\cal{A}$的[[像]]$\operatorname{Im}\cal{A}$ 的[[维数]]称为 $A$ 的[[秩]]，记作 $\operatorname{rank}\cal{A}$.
	- 设 $V$ 和 $V^{\prime}$ 都是[[域]]$F$上$n$ *维* 线性空间, 且 $\cal{A}$ 是 $V$到 $V'$ 的一个[[线性映射]], 
	  logseq.order-list-type:: number
	  则 $\cal{A}$ 是[[单射]]$\Longleftrightarrow\cal{A}$是[[满射]].
		- ## Corollary
		  设 $A$ 是[[域]] $F$ 上[[有限维]][[线性空间]]$V$ 上的一个[[线性变换]], 
		  则 $\cal{A}$ 是[[单射]]$\Longleftrightarrow\cal{A}$是[[满射]].
-
-