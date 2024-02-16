- Any **nonnegative integer power**  of [[binomial]] $(x+y)$ can be expanded into a sum of the form
  $$(x+y)^{n}=\sum_{k=0}^{n}\left(\begin{array}{l}
  n \\
  k
  \end{array}\right) x^{n-k} y^{k}=\sum_{k=0}^{n}\left(\begin{array}{l} 
  n \\
  k
  \end{array}\right) x^{k} y^{n-k}$$
  where $n\in\mathbb{z}, n\geq 0$, and 
  $$\left(\begin{array}{l} n \\ k\end{array}\right) = C_n^k = \frac{n!}{k!(n-k)!} =\frac{n(n-1)\cdots(n-k+1)}{k!}=\prod_{k=1}^{n}\frac{\alpha-k+1}{k}$$
  is known as [[binomial coefficient]].
- A variant is obtained by substituting $1$ for $y$:
  $$(1+x)^{n}=\sum_{k=0}^{n}\left(\begin{array}{l}
  n \\
  k
  \end{array}\right) x^k$$
  which is called the [[binomial series]].
	- 令 $x =1$ 有：
	  $2^{n}=1+C_{n}^{1}+C_{n}^{2}+\cdots+C_{n}^{n}$
	- 令 $x =-1$ 有：
	  $0=1-C_{n}^{1}+C_{n}^{2}+\cdots+(-1)^nC_{n}^{n}$
	- 二者相加推出：
	  $2^{n-1}=1+C_n^2+C_n^4+\cdots$
-