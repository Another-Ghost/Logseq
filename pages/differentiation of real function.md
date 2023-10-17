alias:: 实值函数的微分

- See [[derivative of real function]].
- # Theorem
	- Let $f\in\mathscr{R}$([[Riemann-integrable]]) on $[a, b]$. For $a\leq x \leq b$, put 
	  logseq.order-list-type:: number
	  $$F(x)=\int_{a}^{x}f(t)dt$$ 
	  Then $F$ is [[continuous]] on $[a, b]$; 
	  furthermore, if $f$ is *continuous* at a point $x_0$ of $[a,b]$, then $F$ is [[differentiable]] at $x_0$, and 
	  $$F^{\prime}(x_0)=f(x_0)$$
	- [[fundamental theorem of calculus]]
	  logseq.order-list-type:: number
	  If $f\in \mathscr{R}$([[Riemann-integrable]]) on $[a, b]$ and if there is
	  a [[differentiable]] function $F$ on $[a, b]$ such that $F' = f$, then
	  $$\int_{a}^bf(x)dx=F(b)-F(a)$$
	- Suppose $F$ and $G$ are [[differentiable]] functions on $[a, b]$, $F' = f\in\mathscr{R}$, and $G' = g\in\mathscr{R}$. Then
	  logseq.order-list-type:: number
	  $$\int_a^bF(x)g(x)dx=F(b)G(b)-F(a)G(a)-\int_a^bf(x)G(x)dx.$$
-