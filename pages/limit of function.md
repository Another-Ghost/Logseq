alias:: 极限, 极限值, limit

- # Definition
  id:: 648aa6db-2d2d-4ea0-a6ba-1dd898d9387a
  Let $X$ and $Y$ be [[metric spaces]]; suppose $E\subset X$, $f$ [[maps]] $E$ **into** $Y$, and $p$ is a [[limit point]] of $E$. We write $f(x)\to q$ as $x\to p$, or
  $$\lim_{x\to p}f(x)=q$$
  if there is a **point** $q\in Y$ with the following property: 
  For every $\varepsilon > 0$ there exists a $\delta> 0$ such that
  $$d_Y(f(x),q)<\varepsilon$$
  for **all** points $x\in E$ for which
  $$0< d_X(x, p)<\delta$$
  The symbols $d_X$ and $d_Y$ refer to the [[distances]] in $X$ and $Y$, respectively.
	- > All $x \in E$ for which $0< d_X(x, p)<\delta$ 
	  means both [[right-hand limit]] and [[left hand limit]] should exist.
	- >$X$ and $Y$ are metric space, $E\in X, f: E\to Y,$ 
	  $(\exist p\in\{\mathrm{limitpoint}\mid E\}), (\exist q\in Y),$
	  $(\forall\varepsilon> 0)(\exist\delta> 0)(\forall x\in E)(0< d_X(x,p)<\delta\longrightarrow d_Y(f(x), q)<\varepsilon)$
	- >$\lim_{x\to p}f(x)\ne q$:
	  $(\exist\varepsilon> 0)(\forall\delta> 0)(\exist x\in E)(0< d_X(x,p)<\delta\wedge d_Y(f(x), q)>\varepsilon)$
	- > [sketch map.png](../assets/image_1686059475209_0.png){:height 388, :width 538}
- # Theorem
	- Let $X$ and $Y$ be **metric space**, suppose $E\subset X,  f:E\to Y$, and $p$ is a **limit point** of $E$. Then
	  logseq.order-list-type:: number
	  $$\lim_{x\to p}f(x)=q $$
	  $\Longleftrightarrow$
	  $$\lim_{n\to\infty}f(p_n)=q,$$
	  $\forall$ [[sequence]] $\{p_n\}$ in $E$ such that
	  $$p_n\ne p,\quad\lim_{n\to\infty}p_n=p$$
		- ## Carollary
		  If $f$ has a [[limit]] at $p$, this limit is **unique**.
	- Suppose $E \subset X$, a **metric space**, $p$ is a **limit point** of $E$, $f$ and  $g$ are [[complex functions]] on $E$, and
	  logseq.order-list-type:: number
	  $$\lim_{x\rightarrow p} f(x) =A, \quad \lim _{x \rightarrow p} g(x)=B$$
	  Then
		- $\lim _{x \rightarrow p}(f+g)(x)=A+B$;
		  logseq.order-list-type:: number
		- $\lim _{x \rightarrow p}(f g)(x)=A B$;
		  logseq.order-list-type:: number
		- $\lim _{x \rightarrow p}\left(\frac{f}{g}\right)(x)=\frac{A}{B}$, if $B \neq 0$.
		  logseq.order-list-type:: number
	- Suppose $E \subset X$, a **metric space**,  $p$ is a **limit point** of $E$, $\mathbf{f}$  and  $\mathbf{g}$  **map**  $\mathrm{E}$  into  $R^{k}$, and
	  logseq.order-list-type:: number
	  $$\lim _{x \rightarrow p} \mathbf{f}(x)=\mathbf{L}_{1}, \quad \lim _{x \rightarrow p} \mathbf{g}(x)=\mathbf{L}_{2}$$
	  Then
		- $\lim _{z \rightarrow p}(\mathbf{f}+g)(x)=\mathbf{L}_{1}+\mathbf{L}_{2}$;
		  logseq.order-list-type:: number
		- $\lim _{x \rightarrow p}(\lambda \mathbf{f})(x)=\lambda \mathbf{L}_{1}$, $\forall \lambda$ [[real number]].
		  logseq.order-list-type:: number
		- $\lim _{x \rightarrow p}(\mathbf{f}\cdot\mathbf{g})(x)=\mathbf{L}_1\cdot\mathbf{L}_{2}$
		  logseq.order-list-type:: number