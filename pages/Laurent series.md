public:: true
alias:: 洛朗级数, Laurent expansion, 洛朗展开式

- # Definition
	- Suppose $z_0∈ \mathbb{C}$ and $c_{n}\left(n=0,\pm1,\pm2,\cdots\right)$ are [[complex]] *constants*. A [[series]] of the form
	  $$
	  \sum_{n=-\infty}^{\infty}c_n(z-z_0)^n \tag{1}
	  $$
	  is called the [[Laurent series]] at the *point* $z_0$.
	- There are two parts in [[Laurent series]], one is the [[power series]] $\sum_{n=0}^{\infty}c_{n}(z-z_0)^{n}$ with [[non-negative]] [[exponents]];
	  the other is the power series $\sum_{n=1}^{\infty}c_{-n}(z-z_0)^{-n}$ with [[negative]] *exponents*.
	- If both parts are [convergent]([[series converges]]) at a *point* $z=z_{0}$ , then we say that the *Laurent series* is [convergent] ([[series converges]])at the point.
	- ## [[Radius of Convergence]]
		- If the ^^radius of convergence^^ of $\sum_{n=0}^{\infty}c_{n}(z-z_0)^n$ is $R$ ($R> 0$), then the series [[converges absolutely]] in $|z-z_0|<R$ and [uniformly]([[uniform convergence]]) on every [[compact]] *subset* of this [[disc]]. 
		  Thus, the *sum* of this *series*, $\varphi(z)$, is [[holomorphic]] on $|z-z_0|<R$.
		- Let $\zeta=1/(z-z_0)$. Then
		  $$
		  \sum_{n=1}^{\infty}c_{-n}(z-z_0)^{-n}=\sum_{n=1}^{\infty}c_{-n}\zeta^{n}
		  $$
		  Suppose the [[radius of convergence]] of the above series is $\lambda$ ($\lambda>0$) . 
		  Then the *series* $\sum_{n=1}^{\infty}c_{-n}(z-z_0)^{-n}$ [[converges absolutely]] in $r<|z-z_0|<\infty$ and [uniformly]([[uniform convergence]])on every [[compact]] *subset* of this [[region]] where $r=1/\lambda$. 
		  The *sum* of the *series*, $\psi(z), $is [[holomorphic]] on $r<|z-z_0|<\infty$.
		- If $r>R$, then $(1)$ [diverges]([[series diverges]]) **everywhere**.
		- If $r=R$, then $(1)$ [diverges]([[series diverges]]) **everywhere except** on $|z-z_0|=R$. 
		  There are different circumstances on $|z-a|=R$.
		- If $r<R$ , then $(1)$ [[converges absolutely]] on $r<|z-a|<R$ and [uniformly]([[uniform convergence]]) on every [[compact]] *subset* of this [[annular region]]. 
		  id:: 64c08409-989a-4b0d-8521-29875b4599c8
		  The *series* $(1)$ [[diverges]] on the outside of this region.
			- ### Annulus of Convergence
			  The [[annular region]] $r<|z-z_0|<R$ is called the [[annulus of convergence]] of the *series* $(1)$.
			  By [[Weierstrass Theorem]] , *series* $(1)$ [[converges]] to a [[holomorphic function]] in this [[annulus]]. The function $f(z)=\varphi(z)+\psi(z)$ is [[holomorphic]] in $r<|z-z_0|<R$ .
			- The *series*
			  $$
			  \sum_{n=0}^{\infty}c_{n}(z-z_0)^{n}
			  $$
			  is called the [[holormorphic part]] of $(1)$. The *series* 
			  $$
			  \sum_{n=0}^{\infty}c_{n}(z-z_0)^{n}
			  $$
			  is called the [[principle part]] of $(1)$.
- # Theorem
	- If $f(z)$ is [[holomorphic]] on the [[annulus]] $V=\{z\mid r<|z-z_0|< R(0\le r < R<\infty)\}$, then
	  collapsed:: true
	  $$
	  f(z)=\sum_{n=-\infty}^{\infty}c_{n}(z-z_0)^{n}\tag{2}
	  $$ 
	  on $V$ ([[Laurent expansion]]) , where
	  $$
	  c_{n}=\frac{1}{2\pi i}\oint_C\frac{f(\zeta)d\zeta}{(\zeta-z_0)^{n+1}}$$
	  where $C$ is any [[simple closed curve]] around $z_0$ in $V$.
	  The *series expansion* is [[unique]]. It is called the [[Laurent series]] of $f(z)$ on $V$.
		- # Corollary
		  $f(z)$在$r<|z-z_0|<R$[[解析]], $C: |z-z_0|=r_0(r<r_0<R)$.
		  $$\oint_C f(z)\mathrm{d}z=2\pi i\cdot c_{-1}$$
		  ($c_{-1}$ 为$\frac{1}{z-z_0}$ ( $n=1$ *项* ) 前 *系数* ).