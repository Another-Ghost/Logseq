alias:: infinite series, 级数, 无穷级数

- # Definition
  #SameForComplex
	- Given a [[sequence]] $\{a_n\}$ (of [[complex numbers]]), we associate a **sequence** $\{s_n\}$, where
	  $$s_n=\sum_{k=1}^n a_k$$
	  For $\{s_n\}$ we also use the symbolic expression 
	  $$a_1+a_2+a_3+\cdots$$
	  or
	  $$\sum_{n=1}^\infty a_n$$
	  We call $\sum_{n=1}^\infty a_n$ an [[infinite series]]. 
	  The numbers $s_n$ are called the [[partial sums]] of the series.
	- If ${s_n}$ [[converges]] to $s$, we say that **the series converges**, and write
	  $$\sum_{n=1}^\infty a_n=s$$
	  The number $s$ is called the [[sum of the series]].
		- > $s$ is the [[limit]] of a **sequence** of sums, and is not obtained simply by addition.
	- If $\{s_n\}$ [[diverges]], the **series** is said to **diverge**.
- # Theorem
	- The [[Cauchy criterion]]
	  logseq.order-list-type:: number
	  $\sum a_n$ [[converges]] **if and only if** for every $\varepsilon > 0$ there is an **integer** $N$ such that
	  $$\left|\sum_{k=n}^m a^k \right|\leq\varepsilon$$
	  if $m\geq n\geq N$.
	  In particular, by taking $m = n$,  it becomes 
	  $$\left|a_n\right|\leq\epsilon (n\geq N)$$
	  In other words:
	- $\sum a_n$ [[converges]] $\Longrightarrow\lim_{n\to\infty}a_n = 0$.
	  logseq.order-list-type:: number
	- #real $\sum a_n$ [[converges]](*terms* of $\{a_n\}$ are [[nonnegative]]) $\Longleftrightarrow \{s_n\}$ [[bounded]].
	  logseq.order-list-type:: number
		- > [[comparison test]]
		  For $\{a_n\}, \{b_n\}$ 
		  $a_n, b_n\geq 0, (\exist N_0\in\mathbb{Z})(\forall n\geq N_0)a_n\leq b_n$.
		  $\sum b_n$ [[converges]]$\Longrightarrow \sum a_n$ converges.
		  $\sum a_n$ $diverges\Longrightarrow \sum b_n$ diverges.
		- > [[limit comparison test]]
		  $a_n\geq 0, b_n\ge 0$.
		  $\lim_{n\to\infty}\frac{a_n}{b_n}=L, (L\in \mathbb{R}, \infty)$
		  a. $L\in\mathbb{R}, L\neq 0$,
		  $\sum a_n$ [[converges]] $\Longleftrightarrow \sum b_n$ converges.
		  b. $L=0$,
		  $\sum b_n$ converges $\Longrightarrow \sum a_n$ converges.
		  c. $L=\infty$,
		  $\sum a_n$ converges $\Longrightarrow \sum b_n$ converges.
	- [[root test]]
	  logseq.order-list-type:: number
	  Given $\sum a_n$, put $\alpha = \limsup_{n\to\infty}\sqrt[n]{\left|a_n\right|}$. 
	  Then
		- if $a< 1, \sum a_n$ [[converges]];
		  logseq.order-list-type:: number
		- if $a > 1, \sum a_n$ [[diverges]];
		  logseq.order-list-type:: number
		- if $a = 1$, the test gives no information.
		  logseq.order-list-type:: number
	- [[ratio test]]
	  logseq.order-list-type:: number
	  The series $\sum a_n$
		- [[converges]] if $\limsup_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|\le 1$;
		  logseq.order-list-type:: number
		- [[converges]] if $\liminf_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|\ge 1$;
		  logseq.order-list-type:: number
		- [[diverges]] if $\left|\frac{a_{n+1}}{a_n}\right|\ge 1$ for all $n\ge n_0$, where $n_0$ is some fixed integer.
		  logseq.order-list-type:: number
	- If $\sum a_n = A$, and $\sum b_n = B$, Then
	  logseq.order-list-type:: number
		- $\sum(a_n + b_n) = A + B$;
		  logseq.order-list-type:: number
		- $\sum c a_n = cA$, for any fixed $c$.
		  logseq.order-list-type:: number
	- [[partial sum formula]]
	  logseq.order-list-type:: number
	  Given two sequences  \left\{a_{n}\right\},\left\{b_{n}\right\} , put
	  $$A_{n}=\sum_{k=0}^{n} a_{k}$$
	  if $n \geq 0$;  put $A_{-1}=0$. Then, if $0 \leq p \leq q$, we have
	  $$\sum_{n=p}^{q} a_{n} b_{n}=\sum_{n=p}^{q-1} A_{n}\left(b_{n}-b_{n+1}\right)+A_{q} b_{q}-A_{p-1} b_{p}$$
	- [[Dirichlet's test]]
	  logseq.order-list-type:: number
	  Suppose
		- the [[partial sums]] $A_n$ of $\sum a_n$ form a [[bounded]] sequence;
		  logseq.order-list-type:: number
		- $b_0\geq b_1\geq b_2\geq\cdots$([[decreasing sequence]]);
		  logseq.order-list-type:: number
		- $\lim_{n\to\infty} b_n = 0$.
		  logseq.order-list-type:: number
		- Then $\sum a_n b_n$ [[converges]].
	- Suppose
	  logseq.order-list-type:: number
		- $\left|c_1\right|\geq \left|c_2\right|\geq \left|c_3\right|\geq\cdots$;
		  logseq.order-list-type:: number
		- $c_{2m-1}\geq 0, c_{2m}\leq 0,\ m = 1, 2, 3, \cdots$ ( [[alternating series]]);
		  logseq.order-list-type:: number
		- $\lim_{n\to\infty}c_n = 0$.
		  logseq.order-list-type:: number
		- Then $\sum c_n$ [[converges]].
	- [[Abel test]]
	  logseq.order-list-type:: number
	  If $\sum_{n=0}^{\infty} a_{n}$  [[converges]], and if $\left\{b_{n}\right\}$  is [[monotonic]] and [[bounded]], then $\sum_{n=0}^{\infty} a_{n} b_{n}$  converges.
-