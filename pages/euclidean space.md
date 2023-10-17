alias:: 欧几里得空间, 欧氏空间, euclidean spaces, euclidean k-space

- # Definition
	- For each [[positive integer]] $k$, let$R^k$ be the [[set]] of all [[ordered]]
	  id:: 64fa6aa9-629c-4ab1-baa1-4eb83a45572c
	  k-[[tuples]]
	  $$\mathbf{x} = (x_1, x_2,\cdots x_k)$$
	  where $x_1 , \cdots, x_k$ are [[real numbers]], called the [[coordinates]] of $x$.
	- The elements of $R_k$ are called [[points]], or [[vectors]], especially when $k > 1$.
	- If $$\mathbf{y} = (y_1,\cdots, y_k)$$ and if $\alpha$ is a real number, put:
	  \begin{aligned}
	  \mathbf{x}+\mathbf{y} & =\left(x_{1}+y_{1}, \ldots, x_{k}+y_{k}\right) \\
	  \alpha \mathbf{x} & =\left(\alpha x_{1}, \ldots, \alpha x_{k}\right)
	  \end{aligned}
	  so that $x + y\in R^k$ and $\alpha\mathbf{x}\in R^k$. This defines [[addition]] of vectors, as well as [[multiplication]] of a vector by a real number (a [[scalar]]). These two operations satisfy the [[commutative]], [[associative]], and [[distributive]] laws and make $R^k$ into a [[vector space]] over the [[real field]].
	- The [[zero element]] of $R^k$ is the point $0$, all of whose [[coordinates]] are $0$.
	- We also define the so-called [[inner product]] of $\mathbf{x}$ and $\mathbf{y}$ by
	  id:: 64567235-4999-4746-910c-b238b40ad567
	  $$\mathbf{x}\cdot\mathbf{y}=\sum_{i=1}^{k}x_i y_i$$
	  and the [[euclidean norm]] of $\mathbf{x}$ by 
	  $$|\mathbf{x}|=(x\cdot x)^{1/2}=(\sum_{i}^{k}x_i^2)^{1/2}$$
- [[euclidean spaces]] $R^k$ are the most important examples of [[metric spaces]].
  the [[distance]] in $R^k$ is defined by
  \begin{array}{l}
  d(\mathbf{x}, \mathbf{y})=|\mathbf{x}-\mathbf{y}|=\sqrt{\sum_{k=1}^{n}\left(x_{i}-y_{j}\right)^{2}}\\
  \forall \mathbf{x}=\left(x_{1}, x_{2} \ldots \ldots x_{n}\right), \mathbf{y}=\left(y_{1}, y_{2}, \ldots, y_{n}\right) \in R^{k}
  \end{array}
- The structure now defined (the [[vector space]] $R^k$ with the above [[inner product]] and [[norm]]) is called [[euclidean k-space]].
- # Theorem
  id:: 64777831-9e87-4cdd-98b8-7e17ed21e62b
	- Suppose $\mathbf{x},\mathbf{y},\mathbf{z}\in R^k$, and $\alpha$ is [[real]]. Then
	  logseq.order-list-type:: number
		- $|\mathbf{x}| \ge 0$;
		  logseq.order-list-type:: number
		- $|\mathbf{x}| = 0\Longleftrightarrow \mathbf{x} = \mathbf{0}$;
		  logseq.order-list-type:: number
		- $|\alpha\mathbf{x}| = |\alpha||\mathbf{x}|$;
		  logseq.order-list-type:: number
		- $|\mathbf{x}\cdot\mathbf{y}|\le |\mathbf{x}| |\mathbf{y}|$ ([[Cauchy-Buniakowsky-Schwarz Inequality]]);
		  logseq.order-list-type:: number
		- $|\mathbf{x}+\mathbf{y}|\le |\mathbf{x}| + |\mathbf{y}|$;
		  logseq.order-list-type:: number
		- $|\mathbf{x}-\mathbf{z}|\le |\mathbf{x}-\mathbf{y}| + |\mathbf{y}-\mathbf{z}|$.
		  logseq.order-list-type:: number
	- 在 *n* 维[[欧几里得空间]] $V$ 中，彼此[[正交]]的[[非零向量]]的个数**不超过** $n$ .
	  logseq.order-list-type:: number
- id:: 64ecbfbe-164a-4300-8fed-ee24648c69b2