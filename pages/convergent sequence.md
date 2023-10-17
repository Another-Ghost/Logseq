# Definition
	- A [[sequence]] ${p_n}$ in a [[metric space]] $X$ is said to [[converge]] if $\exist$[[point]] $p\in X$ with the following property: 
	  logseq.order-list-type:: number
	  $\forall\varepsilon > 0, \exist$[[integer]] $N$ such that $n\ge N$ implies that 
	  $$d(p_n, p) < \varepsilon$$
	  (Here $d$ denotes the [[distance]] in $X$.)
		- >$(\exist p\in X)(\forall\varepsilon>0)(\exist N\in\mathbb{Z})(\forall n\ge N)d(p_n, p)<\varepsilon$
		- In this case we also say that ${p_n}$ [[converges]] to $p$, or that $p$ is the [[limit]] of $\{p_n\}$, and we write $p_n\rightarrow p$, or
		  $$\lim_{n\to \infty}p_n = p$$
		- >The definition of ''convergent sequence'' depends not only on ${P_n}$ but also on $X$. In cases of possible ambiguity, we can be more precise and specify ''convergent in X'' rather than ''convergent."
	- If ${p_n}$ does not [[converge]], it is said to [[diverge]].
	  logseq.order-list-type:: number
- # Theorem
	- Let ${p_n}$ be a **sequence** in a **metric space** $X$.
	  logseq.order-list-type:: number
		- ${p_n}$ **converges** to $p\in X\Longleftrightarrow$ $\forall$[[neighborhood]] of $p$ contains $p_n$ **for all but** [[finitely]] many $n$.
		  logseq.order-list-type:: number
		- $p\in X, p'\in X, {p_n}$ **converges** to $p$ and to $p'\ \Longrightarrow\ p' = p$.
		  logseq.order-list-type:: number
		- ${p_n}$ **converges** $\Longrightarrow\ {p_n}$ is [[bounded]].
		  logseq.order-list-type:: number
			- $p_n$ is [[unbounded]] $\Longrightarrow\ p_n$ [[diverges]].
		- If $E\subset X$ and if $p$ is a [[limit point]] of $E$, then there is a [[sequence]] ${p_n}$ in $E$ such that 
		  logseq.order-list-type:: number
		  $$p = \lim_{0\to\infty} p_n$$
	- Suppose  $\left\{s_{n}\right\},\left\{t_{n}\right\}$  are [[complex]] sequences, and  $\lim _{n \rightarrow \infty} s_{n}=s ,  \lim _{n \rightarrow \infty} t_{n}=t$. Then
	  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  $$\lim _{n \rightarrow \infty}\left(s_{n}+t_{n}\right)=s+t$$
		- logseq.order-list-type:: number
		  $$\lim _{n \rightarrow \infty} c s_{n}=c s, \lim _{n \rightarrow \infty}\left(c+s_{n}\right)=c+s$$ for any [[number]]  $c$;
		- logseq.order-list-type:: number
		  $$\lim _{n \rightarrow \infty} s_{n} t_{n}=s t$$
		- logseq.order-list-type:: number
		  $$\lim _{n \rightarrow \infty} \frac{1}{s_{n}}=\frac{1}{s}$$provided  $s_{n} \neq 0(n=1,2,3, \ldots)$, and  $s \neq 0$.
	- ## Convergent Sequence in $R^k$
	  logseq.order-list-type:: number
		- Suppose $\mathbf{x}_{n} \in R^{k}(n=1,2,3, \ldots)$ and
		  logseq.order-list-type:: number
		   $$\mathbf{x}_{n}=(\alpha_{1, n}, \ldots, \alpha_{k, n})$$ 
		  Then $\left\{\mathbf{x}_{n}\right\}$ **converges** to $\mathbf{x}=\left(\alpha_{1}, \ldots, \alpha_{k}\right)$  **if and only if**
		  $$\lim _{n \rightarrow \infty} \alpha_{j, n}=\alpha_{j} \quad(1 \leq j \leq k)$$
		- Suppose $\left\{\mathbf{x}_{n}\right\}, \left\{\mathbf{y}_{n}\right\}$ are sequences in $R^{k}$, $\left\{\beta_{n}\right\}$  is a sequence of [[real numbers]], and $\mathbf{x}_{n} \rightarrow \mathbf{x}, \mathbf{y}_{n} \rightarrow \mathbf{y}, \beta_{n} \rightarrow \beta$. Then
		  logseq.order-list-type:: number
		  $$\lim _{n \rightarrow \infty}\left(\mathbf{x}_{n}+\mathbf{y}_{n}\right)=\mathbf{x}+\mathbf{y}, \quad \lim _{n \rightarrow \infty} \mathbf{x}_{n} \cdot \mathbf{y}_{n}=\mathbf{x} \cdot \mathbf{y}, \quad \lim _{n \rightarrow \infty} \beta_{n} \mathbf{x}_{n}=\beta \mathbf{x}$$
	- $\{p_n\}$ converges to $p\Longleftrightarrow\ \forall$[[subsequence]] of $\{p_n\}$ converges to $p$.
	  logseq.order-list-type:: number
	- ## Subsequence And Compact Metric Space
	  logseq.order-list-type:: number
		- If $\{p_n\}$ is a sequence in a [[compact]] [[metric space]] $X\Longrightarrow\exist$ [[subsequence]] of $\{p_n\}$ converges to a **point** of $X$.
		  logseq.order-list-type:: number
		- $\forall$ [[bounded]] sequence in $R^k$ contains a **convergent subsequence**.
		  logseq.order-list-type:: number
	- ## Monotonic
	  logseq.order-list-type:: number
	  Suppose $\{s_n\}$ is [[monotonic]]. Then ${s_n}$ [[converges]] $\Longleftrightarrow$ it is [[bounded]].
		- > If $\{s_n\}$ is bounded, then it converges to the [[least upper bound]] or [[greatest lower bound]] of its [[range]].
	- (a) If $p>0$, then $\lim _{n \rightarrow \infty} \frac{1}{n^{p}}=0$.
	  logseq.order-list-type:: number
	  (b) If p>0, then $\lim _{n \rightarrow \infty} \sqrt[n]{p}=1$.
	  (c) $\lim _{n \rightarrow \infty} \sqrt[n]{n}=1$.
	  (d) If $p>0$ and $\alpha$ is **real**, then $\lim _{n \rightarrow \infty} \frac{n^{\alpha}}{(1+p)^{n}}=0$.
	  (e) If $|x|<1$, then $\lim _{n \rightarrow \infty} x^{n}=0$.
-