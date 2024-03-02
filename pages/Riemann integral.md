alias:: 黎曼积分, \mathscr{R}

- # definition
	- Suppose $f$ is a [[bounded]] [[real]] function defined on $[a, b]$. Corresponding to each [[partition]] P of $[a, b]$ we put
	  \begin{aligned}
	  M_{i} =\sup f(x),\quad x_ {t-1}\le x \le x_ {i} \\
	  m_{i} =\inf f(x),\quad x_{i-1}\leq x\leq x_{i}
	  \end{aligned}
	  \begin{aligned}
	  U(P,f)& =\sum_{i=1}^nM_i\Delta x_i,  \\
	  L(P,f)& =\sum_{i=1}^nm_i\Delta x_i,  \\
	  \end{aligned}
	  and finally
	  \begin{aligned}
	  \overline{\int}_{a}^{b}fdx=\inf U(P,f),  \\
	  \underline{\int}_{a}^{b}fdx=\sup L(P,f),  \\
	  \end{aligned}
	  where the $\inf$ and the $\sup$ are **taken over all partitions** $P$ of $[a, b]$. 
	  $\overline{\int}_{a}^{b}fdx$ is called the [[upper Riemann integral]] of $f$;  
	  $\underline{\int}_{a}^{b}fdx$ is called the [[lower Riemann integral]].
	- If the [[upper Riemann integral]] and [[lower Riemann integral]] are **equal**, we say that $f$ is [[Riemann-integrable]] on $[a,b]$, we write $f∈\mathscr{R}$ (that is, $\mathscr{R}$ denotes the set of [[Riemann-integrable functions]]), and we denote the common value of $\overline{\int}_{a}^{b}fdx$ and $\underline{\int}_{a}^{b}fdx$ by
	  id:: 64a583d2-387d-452d-a5bc-5213c0460a73
	  $$\int_a^b f dx$$
	  or by
	  $$\int_a^b f(x)dx
	  $$This is the [[Riemann integral]] of $f$ over $[a,b]$.
	- Since $f$ is [[bounded]], there exist two numbers, $m$ and $M$, such that 
	  $$m ≤f(x)≤ M, \quad a ≤x≤b$$
	  Hence, for every $P$,
	  $$m(b-a)\leq L(P,f)\leq U(P,f)\leq M(b-a)$$
	  So that the numbers $L(P,f)$ and $U(P,f)$ form a [[bounded]] set. This shows that the [[upper Riemann integral]] and [[lower Riemann integral]] are **defined for every [[bounded]] function** $f$.
-