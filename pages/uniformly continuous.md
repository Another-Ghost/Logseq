- # Definition
  Let $f$ be a **mapping** of a [[metric space]] $X$ into a metric space $Y$. We say that $f$ is [[uniformly continuous]] on $X$ if for **every** $\varepsilon > 0$ there **exists** $\delta > 0$ such that
  $$d_Y(f(p),f(q)) <\varepsilon$$ 
  for **all** $p$ and $q$ in $X$ for which $d_X(p, q) <\delta$.
- # Theorem
	- Let $f$ be a [[continuous]] mapping of a [[compact]] metric space $X$ into a metric space $Y$. Then $f$ is [[uniformly continuous]] on $X$.
	  logseq.order-list-type:: number
		- > $f$ is **uniformly continuous**, then
			- >$f(X)$ is **closed** and **bounded**.
			- >For $Y=R$, $f$ attains its **maximum** and its **minimum** in $X$.
			- >If $f$ is **1-1**, then $f^{-1}: f(X)\to X$ is [[uniformly continuous]] on $f(X)$.
	- Let $E$ be a [[noncompact]] set in $R^1$ • Then
	  logseq.order-list-type:: number
		- there exists a [[continuous function]] on $E$ which is not [[bounded]];
		  logseq.order-list-type:: number
		- there exists a **continuous** and **bounded** function on $E$ which has no [[maximum]]. 
		  logseq.order-list-type:: number
		- If, in addition, $E$ is **bounded**, then there exists a continuous function on $E$ which is not [[uniformly continuous]].
		  logseq.order-list-type:: number