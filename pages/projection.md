alias:: 投影, projections

- # Theorem
	- 设 $V$ 是[[域]] $F$ 上的一个[[线性空间]], $U$ 和 $W$ 是$V$ 的两个[[子空间]], 且
	  logseq.order-list-type:: number
	  $$
	  V=U\oplus W
	  $$
	  ([[直和]])
	  任取 $\alpha\in V$, 设 $\alpha=\alpha_1+\alpha_2,\alpha_1\in U,\alpha_2\in W$, 令
	  \begin{aligned}
	  \mathcal{P}_U:\ V&\longrightarrow V \\
	  \alpha &\longmapsto α
	  \end{aligned}
	  则 $\mathcal{P}_{U}$ 是 $V$ 上的一个[[线性变换]]。称 $\mathcal{P}_{U}$ 是[[平行]]于 $W$ 在 $U$ 上的[[projection]].
		- 它满足
		  $$
		  \mathcal{P}_{U}\left(\alpha\right)=\begin{cases}\alpha&\quad \alpha\in U
		  \\0&\quad \alpha\in W\end{cases}
		  $$
		  满足上式的 $V$ 上的[[线性变换]]是**唯一**的.
	- 设 $U$ 和 $W$ 是[[域]] $F$ 上[[线性空间]] $V$ 的两个[[子空间]], 且 $V{=}U{\oplus}W$, 则[[平行]]于 $W$ 在 $U$ 上的[[projection]] $\mathcal{P}_{U}$ 与 *平行* $U$ 在 $W$ 上的 *投影* $\mathcal{P}_W$ 是[[正交]]的[[幂等变换]]，且它们的[[和]]等于[[恒等变换]]。
	  logseq.order-list-type:: number
		- **Proof**
			- 设 $U$ 和 $W$ 是[[域]] $F$ 上[[线性空间]] $V$ 的两个[[子空间]]，且 $V=U\oplus W$。
			  平行于 $W$ 在 $\text{U}$ 上的[[projection]] $\mathcal{P}_{U}$ 以及[[平行]]于 $U$ 在$W$ 上的[[projection]] $\mathcal{P}_w$ 具有下述性质:
			  $$
			  \mathcal{P}_{U}^{l}=\mathcal{P}_{U}\\ \mathcal{P}_{\mathrm{W}}^{l}=\mathcal{P}_{\mathrm{W}} \\ \mathcal{P}_{U}\mathcal{P}_{\mathrm{W}}=\mathcal{P}_{\mathrm{W}}\mathcal{P}_{\mathrm{U}}=\mathcal{O}
			  $$
			  即投影 ${\cal P}_{U}$ 和$\mathcal{P}_W$ 是[[正交]]的[[幂等变换]].
			- 任取 $\alpha\in V,$ 设
			  $$
			  \alpha=\alpha_1+\alpha_2,\quad\alpha_1\in U,\alpha_2\in W
			  $$
			  则
			  $$
			  (P_U+P_W)\alpha=P_U\alpha+P_W\alpha=\alpha_1+\alpha_2=\alpha
			  $$
			  因此
			  $$
			  \mathcal{P}_{U}+\mathcal{P}_{W}=\mathcal{I}
			  $$
-