alias:: monotonic

- # Definition
  Let $f$ be [[real]] on $(a, b)$. Then
	- $f$  is said to be [[monotonically increasing]] on $(a, b)$ if $a<x<y<b$ implies  $f(x) \leq f(y)$.
	  logseq.order-list-type:: number
	- $f$ is said to be [[monotonically decreasing]] on $(a, b)$ if $a<x<y<b$ implies  $f(x) \geq f(y)$. 
	  logseq.order-list-type:: number
	- $f$ is said to be [[monotonic]] if $f$ is **monotonically increasing** or **monotonically decreasing**.
	  logseq.order-list-type:: number
- # Theorem
	- Let $f$ be [[monotonically increasing]] on $(a, b)$. Then $f(x+)$([[right-hand limit]]) and
	  logseq.order-list-type:: number
	  $f(x-)$ **exist** at **every point** of $x$ of $(a, b)$. More precisely,
	  $$\sup_{a<t<x} f(t) =f(x-)\le f(x)\le f(x+) = \inf_{x<t<b} f(t)$$
	  Furthermore, if $a < x < y < b$, then
	  $$f(x+)\le f(y-)$$
	  Analogous results evidently hold for [[monotonically decreasing functions]].
		- ## Corollary
		  The [[discontinuities]] of a monotonic function must be [[jump discontinuities]].
	- Let $f$ be [[monotonic]] on $(a, b)$. Then the set of points of $(a, b)$ at which $f$ is [[discontinuous]] is at most [[countable]].
	  logseq.order-list-type:: number