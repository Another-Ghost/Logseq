alias:: 插值余项定理

- # Theorem
  Suppose $f$ is a [[real]] function on $[a, b]$, $n$ is a **positive integer**, f^{(n-1)} is [[continuous]] on $[a, b]$, $f^{(n)}(x)$ exists for every $t\in(a, b)$. Let $\alpha$, $\beta$ be *distinct points* of $[a, b]$, and define
  $$P(x)=\sum_{k=0}^{n-1}\frac{f^{(k)}(\alpha)}{k!}(x-\alpha)^k$$
  Then there exist a point $c$ between $\alpha$ and $\beta$ such that
  $$f(\beta)=P(\beta)+\frac{f^{(n)}(c)}{n!}(\beta-\alpha)^n$$
  For $n = 1$, this is just the [[Lagrange mean value theorem]]. 
  In general, the theorem shows that $f$ can be **approximated** by a [[polynomial]] of [[degree]] $n - 1$, and that allows us to estimate the [[error]], if we know [[bounds]] on $\left|f^{(n)}(x)\right|$.
	- >If $f$ is a [[polynomial]], then:
	  $$f(x)=\sum_{k=0}^{n}\frac{f^{(k)}(0)}{k!}x^k,\quad n=1,2,\cdots$$
- # Corollary
  Let $f$ is a [[real]] function on $[a, b]$ Suppose for each  $n\in N$, $f^{(n)}(x)$ exists for every $x \in[a, b]$ and there exists $M>0$ such that $\left|f^{(n)}(x)\right| \leq M$, for all $x \in[a, b]$, $n \in N$. Then the [[Taylor series]] $\sum_{n=0}^{\infty} \frac{f^{(n)}(\alpha)}{n !}(x-\alpha)^{n}$  [[converges]] to $f(x)$, for all $x \in[a, b]$.
	- > Function $f$ is called [[analytic function]] if its Taylor series converges to itself.