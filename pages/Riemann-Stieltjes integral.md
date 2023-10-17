alias:: Stieltjes integral, 积分

- # Definition
	- Let $α$ be a [[monotonically increasing]] [[function]] on $[a,b]$ (since $α(a)$ and $α(b)$ are [[finite]], it follows that $\alpha$ is [[bounded]] on $[a, b])$. Corresponding to each [[partition]] $P$ of $[a,b]$, we write
	  $$\Delta\alpha_i=\alpha(x_i)-\alpha(x_{i-1})$$
	  It is clear that $\Delta\alpha_i≥0$.
	- For any [[real]] function $f$ which is [[bounded]] on $[a, b]$ we put
	  \begin{aligned}
	  M_{i} =\sup f(x),\quad x_ {t-1}\le x \le x_ {i} \\
	  m_{i} =\inf f(x),\quad x_{i-1}\leq x\leq x_{i} \\
	  U(P,f,\alpha)=\sum_{i=1}^nM_i\Delta\alpha_i \\
	  L(P,f,\alpha)=\sum_{i=1}^nm_i\Delta\alpha_i \\ 
	  \end{aligned}
	  We define
	  \begin{aligned}
	  \overline{\int}_{a}^{b} f dα = \inf U(P, f, α) \\
	  \underline{\int}_a^bfd\alpha=\sup L(P,f,\alpha),
	  \end{aligned}
	  the $\inf$ and $\sup$ are taken over all partitions.
	  > $$M_i-m_i=\sup\left\{f(x)-f(y)|x,y\in[x_{i-1}, x_i]\right\}$$
	- If $\overline{\int}_{a}^{b} f dα = \underline{\int}_a^bfd\alpha$, we denote their common value by
	  $$\int_{b}^{a}fdx$$
	  or sometimes by
	  $$\int_{a}^{b} f(x) d\alpha(x)$$
	  This is the [[Riemann-Stieltjes integral]] of $f$ with respect to $α$, over $[a,b]$.
	- if $\int_{b}^{a}fdx$ exists, we say that $f$ is [[integrable]] with respect to $\alpha$ and write $f\in\mathscr{R}(\alpha)$([[Riemann-integrable function]]).
	- ## Riemann-Stieltjes & Riemann
	  By taking $\alpha(x) = x$, the [[Riemann integral]] is seen to be a **special case** of the [[Riemann-Stieltjes integral]].
- # Theorem
  Without saying so every time, $f$ will be assumed [[real]] and [[bounded]], and $\alpha$ [[monotonically increasing]] on $[a, b]$; and, when there can be no misunderstanding, we shall write $\int$ in place of $\int_{a}^{b}$.
	- If $P^*$ is a [[refinement]] of $P$, then 
	  logseq.order-list-type:: number
	  $$L(P, f, \alpha)\le L(P^*, f, \alpha)$$
	  $$U(P^*,f,\alpha)\le U(P,f,\alpha)$$
	- logseq.order-list-type:: number
	  $$\overline{\int}_{a}^{b} f dα\le\underline{\int}_a^bfd\alpha$$
	- $f\in\mathscr{R}(\alpha)$([[Riemann-integrable]]) on $[a, b]$ **if and only if** for every $\varepsilon > 0$ there exists a [[partition]] $P$ such that
	  logseq.order-list-type:: number
	  $$U(P,f,\alpha) - L(P,f, \alpha) < \varepsilon$$
	- Theorem
	  logseq.order-list-type:: number
		- If $U(P,f,\alpha) - L(P,f, \alpha) < \varepsilon$ holds for some $P$ and some $E$,then it holds (with the same $\varepsilon$ for every [[refinement]] of $P$.
		  logseq.order-list-type:: number
		- If $U(P,f,\alpha) - L(P,f, \alpha) < \varepsilon$ holds for $P = {x_0,\cdots,x_n}$ and if $s_i,t_i$ are arbitrary points in $[x_{i-1},x_i]$, then
		  logseq.order-list-type:: number
		  id:: 64a31ce7-e103-4eab-965f-7e64bcc0a2e6
		  $$\sum_{i=1}^n|f(s_i)-f(t_i)|\mathrm{~}\Delta\alpha_i<\varepsilon$$
		- If $f∈ \mathscr{R}(α)$([[Riemann integral]]) and the hypotheses of [b.](64a31ce7-e103-4eab-965f-7e64bcc0a2e6) hold, then
		  logseq.order-list-type:: number
		  $$\left|\sum_{i=1}^nf(t_i)\mathrm{~}\Delta\alpha_i-\int_a^bf\mathrm{~}d\alpha\right|<\varepsilon.$$
	- If $f$ is [[continuous]] on $[a, b]$ then $f\in\mathscr{R}(\alpha)$([[Riemann-integrable]]) on $[a, b]$.
	  logseq.order-list-type:: number
	- If $f$ is [[monotonic]] on $[a, b]$, and if $\alpha$ is [[continuous]] on $[a, b]$, then $f\in\mathscr{R}(\alpha)$([[Riemann-integrable]]).
	  logseq.order-list-type:: number
	- Suppose $f$ is [[bounded]] on $[a, b]$, $f$ has only [[finitely]] many points of [[discontinuity]] on $[a, b]$, and $\alpha$ is [[continuous]] at every point at which $f$ is [[discontinuous]]. Then $f\in\mathscr{R}$([[Riemann-integrable]]).
	  logseq.order-list-type:: number
	- Suppose $f\in\mathscr{R}(\alpha)$([[Riemann-integrable]]) on $[a, b]$, $m\le f\le  M$, $\phi$ is [[continuous]] on $[m, M]$, and $h(x) = \phi(f(x))$ on $[a, b]$. Then $h\in\mathscr{R}(\alpha)$ on $[a, b]$.
	  logseq.order-list-type:: number
	- [[Change of variable]]
	  logseq.order-list-type:: number
	  id:: 64a6ef2a-9105-4873-8c73-4e24605abbb0
	  Suppose $\phi$ is a [[strictly increasing]] [[continuous]] function that maps an *interval* $[A, B]$ *onto* $[a, b]$. Suppose $\alpha$ is [[monotonically increasing]] on $[a, b]$ and $f\in\mathscr{R}(\alpha)$ on $[a, b]$. Define $\beta$ and $g$ on $[A, B]$ by
	  $$\beta(y) = \alpha(\phi(y)),\quad g(y) = f(\phi(y))$$
	  Then $g\in\mathscr{R}(\beta)$ and 
	  $$\int_A^Bgd\beta=\int_a^bfdx$$
	  >Take $\alpha(x)=x$. Then $\beta=\varphi$. Assume $\varphi'\in\mathscr{R}$ on $[A,B]$, by the previous two theorems, we obtain
	  $$\int_a^bf(x)dx=\int_A^B gd\beta=\int_a^bf(\varphi(y))\varphi^{\prime}(y)dy$$