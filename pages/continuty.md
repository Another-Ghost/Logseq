alias:: continuous, 连续

- # Definition
  Suppose $X$ and $Y$ are [[metric spaces]], $E\subset X$, $p\in E$, and [[function]] $f$ **maps** $E$ **into** $Y$. Then $f$ is said to be [[continuous]] **at** $p$ if for every $\varepsilon > 0$ there exists a $\delta > 0$ such that 
  $$d_Y(f(x),f(p)) < \varepsilon$$ 
  for all [[points]] $x\in E$ for which $d_X(x, p) < \delta$.
- If $f$ is continuous at **every point** of $E$, then $f$ is said to be [[continuous on]] $E$.
- >$X$ and $Y$ are metric space, $E\in X, f: E\to Y, p\in E,$
  $$(\forall\varepsilon>0)(\exist\delta>0)(\forall x\in E)\ d_X(x, p)<\delta\longrightarrow d_Y(f(x), f(p))<\varepsilon$$
- >If $f$ is [[continuous]] at $p$, then $f$ is defined at $p$.
- >If $p$ is an [[isolated point]] of $E$, then f is [[continuous]] at $p$.
- >If $p$ is a [[limit point]] of $E$, then $f$ is [[continuous]] at $p$ **if and only if** $\lim_{x\to p}f(x) = f(p)$([[limit of function]]).
- # Theorem
	- A [[mapping]] $f$ of a metric space $X$ into a metric space $Y$ is [[continuous]] **on** $X$ **if and only if**  $f^{-1}(V)$([[inverse]]) is [[open]] in $X$ for **every** [[open]] set $V\subset Y$.
	  logseq.order-list-type:: number
		- ## Corollary
		  A mapping $f$ of a metric space $X$ into a metric space $Y$ is [[continuous]] **if and only if** $f^{-1}(C)$ is [[closed]] in $X$ for **every closed set** $C\subset Y$.
	- Let $f$ and $g$ be [[complex continuous functions]] on a metric space $X$. Then $f + g$([[addition]]), $fg$([[multiplication]]), and $f/g$ are **continuous** on $X$.
	  logseq.order-list-type:: number
	- **Continuty on** $R^k$
	  logseq.order-list-type:: number
		- Let $f_1,\cdots, f_k$ be [[real functions]] on a metric space $X$, and let $f$ be the mapping of $X$ into $R^k$ defined by
		  logseq.order-list-type:: number
		  $$\mathbf{f}(x)=(f_1(x),\cdots,f_k(x),\quad (x\in X)$$
		  then $\mathbf{f}$ is [[continuous function]] **if and only if** each of the functions $f_1,\cdots, f_2$ is **continuous**.
		- If $f$ and $g$ are [[continuous function]] mappings of $X$ into $R^k$, then $f + g$ and $f · g$ are **continuous** on $X$.
		  logseq.order-list-type:: number
- # continuity and compactness
	- Suppose $f$ is a [[continuous mapping]] of a [[compact]] [[metric space]] $X$ into a metric space $Y$. Then $f(X)$ is **compact**.
	  logseq.order-list-type:: number
	- If $X$ is a [[compact]] metric space and $\mathbf{f}: X\to R^k$ is a [[continuous]], then $\mathbf{f}(X)$ is [[closed]] and [[bounded]].
	  logseq.order-list-type:: number
	- [[extreme value theorem]]
	  logseq.order-list-type:: number
	  Let $X$ be a [[compact]] metric space. Suppose $f:X\to R$ is [[continuous]], and
	  $$M=\sup_{p\in X}f(p), m=\inf_{p\in X}f(p)$$
	  Then there exist points $p, q\in X$ such that $f(p) = M$ and $f(q) = m$.
	- Suppose  $f$  is a [[continuous]] [[1-1 mapping]] of a [[compact]] metric space  $X$  **onto** a metric space  $Y$. Then the [[inverse]] mapping $f^{-1}$  defined on $Y$ by 
	  logseq.order-list-type:: number
	  $$f^{-1}(f(x))=x \quad(x \in X)$$ 
	  is a **continuous** mapping of $Y$ **onto** $X$.
- # Continuity and Connectedness
	- If $f$ is a [[continuous mapping]] of a metric space $X$ into a metric space $Y$, and if $E$ is a [[connected]] subset of $X$, then $f(E)$ is **connected**.
	  logseq.order-list-type:: number
	- ### [[intermediate value theorem]]
	  logseq.order-list-type:: number
	  Let $f$ be a [[real continuous function]] on the [[interval]] $[a, b]$. If $f(a)<f(b)$ and if $c$ is a [[number]] such that $f(a)<c<f(b)$, then there exists a point $x \in(a, b)$ such that $f(x)=c$.
	  A similar result holds, of course, if $f(a)>f(b)$.
-
-