alias:: 幂级数

- #SameForComplex
- # Definition
  Given a **sequence** $\{c_n\}$ of **complex numbers**, the [[series]]
  $$\sum_{n=0}^\infty c_n z^n$$
  is called a [[power series]]. The number $c_n$ are called the [[coefficients of the series]]; $z$ is a **complex number**.
- # Theorem
	- [[Abel Theorem]]
	  logseq.order-list-type:: number
	  Given the **power series** $\sum c_n z^n$, put
	  \begin{aligned}
	  \alpha &=\limsup_{n\to\infty}\sqrt[n]{\left|c_n\right|} \\
	   R &=\frac{1}{\alpha}
	  \end{aligned}
	  (If $\alpha = 0, R =+\infty$; if $\alpha = +\infty, R = 0$.) Then $\sum c_nz^n$ [[converges]] if $|z| < R$, and [[diverges]] if $\left|z\right| > R$.
		- $R$ is called the [[radius of convergence]] of $\sum c_n z^n$.
	- $f(z)=\sum_{n=0}^{\infty}c_nz^n$ is [[analytic]] if $|z|\le R$([[radius of convergence]]).
	  logseq.order-list-type:: number
-