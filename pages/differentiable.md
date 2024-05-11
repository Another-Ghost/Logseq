public:: true
alias:: first order approximation, differentiability, 可导, 可微, 可微函数, 可微性

- >See [[derivative of real function]]
- > If $f$ is [[differentiable]] at $c$, we have
  $$f^\prime(c)=\lim_{x\to c}\frac{f(x)-f(c)}{x-c}$$
  $$\lim_{x\to c}\left[\frac{f(x)-f(c)}{x-c}-f^\prime(c)\right]=0$$
  $$\lim_{x\to c}\frac{f(x)-\left[f(c)+f^{\prime}(c)(x-c)\right]}{x-c} =0$$
   Then $\exists \phi:(a, b) \rightarrow R$ 
  $$\phi(x)=\frac{f(x)-\left[f(c)+f^{\prime}(c)(x-c)\right]}{x-c}$$
  which is [[continuous]] at $c$ such that
  $$f(x)=f(c)+f^{\prime}(c)(x-c)+(x-c) \phi(x)$$
  for all  $x \in(a, b)$, with $\phi(c)=0$.
- ## 总结
- ### 可微和可导
	- 在[[一元函数]]的情境中，可微性和可导性是**等价**的。这两个概念通常被用来描述函数在某一点的局部线性行为，具体来说：
		- **可导性**：如果一个实值函数 \( f(x) \) 在某一点 \( a \) 有导数，即极限
		  logseq.order-list-type:: number
		  $$\lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$$
		  存在，那么我们说函数 \( f \) 在点 \( a \) 是可导的。这意味着函数在该点的变化率可以通过一个具体的实数来描述。
		- **可微性**：在一元函数的情况下，如果函数在某一点可导，那么它在该点也是可微的。具体来说，函数 \( f \) 在点 \( a \) 可微意味着存在一个线性映射（在一维情况下就是乘以某个常数），使得
		  logseq.order-list-type:: number
		  $$\lim_{h \to 0} \frac{|f(a+h) - f(a) - Lh|}{|h|} = 0,$$
		  其中 \( L \) 是 \( f \) 在 \( a \) 点的导数。这个定义实际上是可导性定义的一个直接结果。
		- **等价性**：在一维的实分析中，函数在某点可导通常意味着它在该点可微，反之亦然。导数 \( f'(a) \) 本质上是描述 \( f \) 在 \( a \) 点的最佳线性逼近的斜率。
		  logseq.order-list-type:: number
	- **多元函数的情况**：在多变量的情况下，可微性与可导性的关系更加复杂。一个多元函数在某点可微意味着它在该点不仅各个方向的偏导数存在，而且这些偏导数组合起来能够形成一个线性映射，称为该点的微分或雅可比矩阵。如果一个多元函数在某点的所有偏导数存在且连续，那么该函数在该点可微。但仅仅偏导数存在并不一定保证函数在该点可微。
-