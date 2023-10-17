alias:: metric spaces, 度量空间

- # Definition
	- A [[set]] $X$, whose [[elements]] we shall call [[points]], is said to be a [[metric space]] if with any two points $p$ and $q$ of $X$ there is associated a [[real number]] $d(p, q)$, called the [[distance]] from $p$ to $q$, such that: 
	  logseq.order-list-type:: number
	  id:: 648aa6dc-d82f-4d78-bc1d-98fc41f1303b
		- [[Non-negativity]] $d(p, q) > 0$ if $p\ne q$;    $d(p, p) = 0$;
		  logseq.order-list-type:: number
		- [[Symmetry]] $d(p, q) = d(q, p)$;
		  logseq.order-list-type:: number
		- The [[Triangle Inequality]] $d(p, q)\le d(p, r) + d(r, q)$, for any $r\in X$.
		  logseq.order-list-type:: number
		- Any [[function]] with these three properties is called a [[distance function]], or a [[metric]].
- # Theorem
- 1. Every [[interior points]] of the [[set]] $E$ is also a [[limit point]] of $E$.
  2. Every [[neighborhood]] is an [[open]] [[set]].
  3. If $p$ is a [[limit point]] of a set $E$, then every [[neighborhood]] of $p$ contains [[infinitely]] many points of $E$.
	- ## Corollary
	  A [[finite]] point set has no [[limit points]].
- 4. A set $E$ is [[open]] **if and only if** its [[complement]] is [[closed]].
- 5.
	- (a) For any collection  $\left\{G_{\alpha}\right\}$  of [[open]] sets,  $\bigcup_{\alpha} G_{\alpha}$  is open.
	- (b) For any collection  $\left\{F_{\alpha}\right\}$  of [[closed]] sets,  $\bigcap_{\alpha} F_{\alpha}$  is closed.
	- (c) For any [[finite]] collection  $G_{1}, \cdots, G_{n}$  of [[open]] sets,  $\bigcap_{i=1}^{n} G_{i}$  is open.
	- (d) For any [[finite]] collection  $F_{1}, \cdots, F_{n}$  of [[closed]] sets,  $\bigcup_{i=1}^{n} F_{i}$  is closed.
- 6. Suppose $E\subset Y\subset X$. $E$ is [[open]] **relative to** $Y\Longleftrightarrow E = Y\cap G$ for some open subset $G$ of $X$.
- >Only $\emptyset$ and $R$ are both [[open]] and [[closed]].