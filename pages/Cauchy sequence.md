# Definition
	- A [[sequence]] $\{p_n\}$ in a [[metric space]] $X$ is said to be a [[Cauchy sequence]] if for every $\varepsilon > 0$ there is an [[integer]] $N$ such that $d(p_n , p_m)<\varepsilon$ if $n\ge N$ and $m\ge N$.
- # Theorem
- If $\{p_n\}$ is a sequence in $X$ and if $E_N$ consists of the points $p_N, p_{N+1} ,p_{N+2},\cdots$, $\{p_n\}$ is a Cauchy sequence **if and only if** 
  logseq.order-list-type:: number
  $$\lim_{N\to\infty}\mathrm{diam}\ E_N= 0$$
- In any metric space $X$, every [[convergent sequence]] is a Cauchy sequence.
  logseq.order-list-type:: number
  >Cauchy sequence 不一定收敛
- If $X$ is a [[compact]] metric space and if $\{p_n\}$ is a Cauchy sequence in $X$,
  logseq.order-list-type:: number
  then $\{p_n\}$ **converges** to some point of $X$.
- In $R^k$, every Cauchy sequence **converges**([[completeness]]).
  logseq.order-list-type:: number
-
-