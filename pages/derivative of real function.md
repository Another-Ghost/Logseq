# Definition
	- Let [[function]] $f$ be defined (and [[real-valued]]) on $[a, b]$. For any $x\in[a, b]$ form the [[quotient]]
	  $$\phi(t)=\frac{f(t)-f(x)}{t-x} \quad(a<t<b, t \neq x)$$
	  and define
	  $$f^{\prime}(x)=\lim _{t \rightarrow x} \phi(t)$$
	  **provided** this [limit]([[limit of function]]) **exists**.
	  We thus associate with $f$ a [[function]] $f^{'}$ whose [[domain]] is the set of [[points]] $x$ at which the **limit exists**; $f'$ is called the [[derivative]] of $f$.
	- If $f^{'}$ is **defined at a point** $x$, we say that $f$ is [[differentiable]] **at** $x$. If $f^{'}$ is **defined at every point** of a set $E\subset [a, b]$, we say that $f$ is [[differentiable]] **on** $E$.
	  id:: 64b2a841-7fd5-4e39-8350-860ae779e65e
		- It is possible to consider [[right-hand limit]] and [[left-hand limit]]; this leads to the definition of [[right-hand derivative]] and [[left-hand derivative]]. 
		  In particular, at the [[endpoints]] $a$ and $b$, the derivative, if it exists, is a [right-hand]([[right-hand derivative]]) or [[left-hand derivative]], respectively.
- # Theorem
	- Let $f$ be defined on $[a, b]$. If $f$ is [[differentiable]] at a point $x\in [a, b]$, then $f$ is [[continuous]] at $x$.
	  logseq.order-list-type:: number
	  >This is still true when $f$ is a [[complex]] function.
	- Suppose $f$ and $g$ are defined on $[a, b]$ and are [[differentiable]] at a
	  logseq.order-list-type:: number
	  collapsed:: true
	  point $x\in [a, b]$. Then $f+ g$, $fg$, and $f/g$ are **differentiable** at $x$, and
		- $(f + g)'(x) = f'(x) + g'(x)$;
		  logseq.order-list-type:: number
		- $(fg)'(x) = f'(x)g(x) + f(x)g'(x)$;
		  logseq.order-list-type:: number
		- $\left(\frac{f}{g}\right)'(x) = \frac{g(x)f'(x) - g'(x)f(x)}{g^2(x)}$, if $g(x)\ne 0$.
		  logseq.order-list-type:: number
	- Suppose $f$ is continuous on $[a, b]$, $f'(x)$ exists at some point $x\in [a, b]$, $g$ is defined on an [[interval]] $I$ which contains the [[range]] of $f$, and $g$ is [[differentiable]] at the point $f(x)$. If 
	  logseq.order-list-type:: number
	  collapsed:: true
	  $$h(t) = g(f(t)),\quad a\le t\le b$$
	  then $h$ is [[differentiable]] at $x$, and
	  $$h'(x)=g'(f(x))f'(x)$$
	  ([[composition]])
		- > [proof](https://www.bilibili.com/video/BV1px411C7bL?t=1673.7&p=21)
	- Let $f$ be defined on $[a, b]$; if $f$ has a [[local maximum]] at a point $x\in (a, b)$, and if $f'(x)$ **exists**([[differentiable]]), then $f'(x) = 0$.
	  logseq.order-list-type:: number
	  The analogous statement for [[local minima]] is of course also true.
	- Suppose $f$ is [[differentiable]] in $(a, b)$.
	  logseq.order-list-type:: number
	  collapsed:: true
		- If $f'(x)\ge 0$ for all $x\in (a, b)$, then $f$ is [[monotonically increasing]].
		  logseq.order-list-type:: number
		- If $f'(x) = 0$ for all $x\in (a, b)$, then $f$ is [[constant]].
		  logseq.order-list-type:: number
		- If $f'(x)\le 0$ for all $x\in (a, b)$, then $f$ is [[monotonically decreasing]].
		  logseq.order-list-type:: number
	- [[Darboux's Theorem]]
	  logseq.order-list-type:: number
	  collapsed:: true
	  Suppose $f$ is a [[real]] [[differentiable]] function on $[a, b]$ and suppose
	  $f'(a) <\lambda <f'(b)$. Then there is a point $x\in (a, b)$ such that $f'(x) = \lambda$.
	  A similar result holds of course if $f'(a) > f'(b)$.
		- >That is, the [[image]] of the [[derivative]] $f'$ is an [[interval]].
		- > If a $f$ does not satisty the precondition of [[Darboux's Theorem]] , it can not be [[derivative]] of any function (There is no **solution** to $y'=f(x)$).
		- # Corollary 
		  If $f$ is [[differentiable]] on $[a, b]$, then $f'$ cannot have any [[simple discontinuities]] on $[a, b]$.
	- [[L'Hospital's rule]]
	  logseq.order-list-type:: number
	  collapsed:: true
	  $f$ and $g$ are [[real]] and [[differentiable]] in $(a, b)$, and $g^{\prime}(x) \neq 0$ for all $x \in(a, b)$, where $-\infty \leq a<b \leq+\infty$. Suppose 
	  $$\frac{f^{\prime}(x)}{g^{\prime}(x)}\rightarrow A \text { as } x \rightarrow a\text{.}$$
	  If
	  $$f(x) \rightarrow 0 \text { and } g(x) \rightarrow 0 \text { as } x \rightarrow a$$
	  or if
	  $$g(x) \rightarrow+\infty \text { as } x \rightarrow a$$
	  then
	  $$\frac{f(x)}{g(x)} \rightarrow A \text { as } x \rightarrow a$$
		- The analogous statement is of course also true if $x \rightarrow b$, or if $g(x) \rightarrow-\infty$.
- # [[derivative of higher order]]