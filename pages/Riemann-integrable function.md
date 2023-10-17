alias:: Riemann-integrable, Riemann-integrable functions

- # Theorem
	- ## Formula
	  logseq.order-list-type:: number
		- If $f_1\in Re(\alpha)$ and $f_2 ∈\mathscr{R}(α)$ on $[a,b]$, then
		  logseq.order-list-type:: number
		  $$
		  f_1+f_2\in\mathscr{R}(\alpha),
		  $$
		  $cf ∈ \mathscr{R}(α)$ for every *constant* $c$, and
		  $$
		  \int_a^b(f_1+f_2)\:d\alpha=\int_a^bf_1\:d\alpha+\int_a^bf_2\:d\alpha
		  $$
		  $$\int_a^bcfd\alpha=c\int_a^bfd\alpha$$
		- If $f_1(x)≤f_2(x)$ on $[a,b]$, then
		  logseq.order-list-type:: number
		  $$\int_a^bf_1\mathrm{~}d\alpha\leq\int_a^bf_2\mathrm{~}d\alpha$$
		- If $f∈ \mathscr{R}(α)$ on $[a,b]$ and if $a<c<b$, then $f\in \mathscr{R}(α)$ on $[a,c]$ and on $[c,b]$, and
		  logseq.order-list-type:: number
		  $$\int_{a}^cfd\alpha+\int_{c}^bfd\alpha=\int_a^bfd\alpha$$
		- If $f\in\mathscr{R}(α)$ on $[a, b]$ and if $\left|f(x)\right| ≤ M$ on $[a,b]$, then
		  logseq.order-list-type:: number
		  $$\left|\int_{a}^bfd\alpha\right|\le M\left[\alpha(b)-\alpha(a)\right]$$
		- If $f∈ \mathscr{R}(α_1)$ and $f∈ \mathscr{R}(α_2), then $f∈ \mathscr{R}R(α_1+ α_2)$ and
		  logseq.order-list-type:: number
		  $$\int_a^bfd(\alpha_1+\alpha_2)=\int_a^bfd\alpha_1+\int_a^bfd\alpha_2$$
		  if $f∈ \mathscr{R}(α)$ and $c$ is a [[positive]] *constant*, then $f∈\mathscr{R}(c\alpha)$ and
		  $$\int_a^bfd(c\alpha)=c\int_a^b fd\alpha$$
	- If $f\in\mathscr{R}(\alpha)$ and $g\in\mathscr{R}(\alpha)$ on $[a,b]$, then
	  logseq.order-list-type:: number
		- $fg\in\mathscr{R}(\alpha)$;
		  logseq.order-list-type:: number
		- $\left|f\right|\in\mathscr{R}(\alpha)$ and $\left|\int_a^bfd\alpha\right|\leq\int_a^b|f|d\alpha$.
		  logseq.order-list-type:: number
	- If $a < s < b$, $f$ is [[bounded]] on $[a, b]$, $f$ is [[continuous]] at $s$, and $\alpha(x) = I(x - s)$, then 
	  logseq.order-list-type:: number
	  $$\int_a^b f d\alpha =f(s)$$
	  > [Proof](https://www.bilibili.com/video/BV1R44y1i7gq?t=4732.4)
	- Suppose $c_n≥0$ for $1,2,3,...$, $\sum c_n$ [[converges]], $\left\{s_n\right\}$ is a [[sequence]] of distinct points in $(a,b)$, and
	  logseq.order-list-type:: number
	  $$\alpha(x)=\sum_{n=1}^\infty c_nI(x-s_n)$$
	  Let $f$ be [[continuous]] on $[a,b]$. Then
	  $$\int_a^bf\:d\alpha=\sum_{n=1}^\infty c_nf(s_n)$$
	- Assume $α$ [[increases monotonically]] and $\alpha'∈\mathscr{R}$([[derivative]]) on $[a,b]$. Let $f$ be a [[bounded]] [[real]] function on $[a,b]$. 
	  logseq.order-list-type:: number
	  Then $f∈ \mathscr{R}(α)$ **if and only if** $f\alpha'∈ \mathscr{R}$. In that case
	  $$\int_a^bfd\alpha=\int_a^bf(x)\alpha^{\prime}(x)dx.$$
-
-