alias:: product of series

- # Definition
  Given $\sum a_n$ and $\sum b_n$, we put 
  $$c_n=\sum_{k=0}^{n}a_k b_{n-k},\quad n=0, 1, 2, \cdots$$
  and call $\sum c_n$the [[Cauchy product]] of the two given [[series]].
- # Theorem
	- [[Mertens test]]
	  logseq.order-list-type:: number
	  Suppose
		- $\sum_{n=0}^{\infty} a_n$ [[converges absolutely]],
		  logseq.order-list-type:: number
		- $\sum_{n=0}^{\infty} a_n = A$,
		  logseq.order-list-type:: number
		- $\sum_{n=0}^{\infty} b_n = B$,
		  logseq.order-list-type:: number
		- $c_n=\sum_{k=0}^{n}a_kb_{n-k},\ n=0,1,2,\cdots$
		  logseq.order-list-type:: number
		- Then
		  $$\sum_{n=0}^{\infty}c_n=AB$$
	- [[Abel test]]
	  logseq.order-list-type:: number
	  If the series $\sum a_n, \sum b_n, \sum c_n$ [[converge]] to $A, B, C$, and $c_n = a_0b_0+\cdots+a_nb_n$ then $C = AB$.
-