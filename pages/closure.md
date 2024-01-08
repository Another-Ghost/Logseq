alias:: 闭包

- # 拓扑学中的闭包
	- # Definition
	  If $X$ is a [[metric space]], if $E\subset X$, and if $E'$ denotes the set of all [[limit points]] of $E$ in $X$, then the [[closure]] of $E$ is the set $\bar{E} = E\cup E'$.
	- # Theorem
		- 1.
			- If $X$ is a [[metric space]] and $E\subset X$, then
				- (a) $\bar{E}$ is [[closed]],
				- (b) $E = \bar{E}\Longleftrightarrow$ $E$ is closed,
				- (c) $\bar{E}\subset F$ for every closed set $F\subset X$ such that $E\subset F$.
			- By $(a)$ and $(c)$, $E$ Is the **smallest closed subset** of $X$ that contains $E$.
		- 2. Let $E$ be a **nonempty** set of [[real numbers]] which is [[bounded above]]. Let $y =\mathrm{sup}\ E$ (Then $y\in \bar{E}$). Hence $y\in E$ **if** $E$ is [[closed]].
- # 代数学中的闭包
	- 在代数学中，特别是在线性代数中，闭包有不同的含义。对于一个[[集合]]，它的闭包是指通过在集合上进行特定[[运算]]所能到达的**所有元素的集合**。
		- ### [[线性闭包]]
		- 一个向量集的线性闭包是指由这些向量通过线性组合所能构成的所有向量的集合。这通常与前面提到的“生成空间”（Span）是一样的。
	- **性质**：
		- 一个集合的线性闭包是一个向量空间。
		- 它是包含原始集合的最小向量空间。