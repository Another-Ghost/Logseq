alias:: holomorphic, 全纯函数, 全纯

- 全纯函数（Holomorphic function）是复分析中的一个核心概念，指定义在复数域中的函数，具有在其定义域内处处复可微的性质。全纯函数也被称为[[解析函数]]（Analytic function）。
- ### 定义
  设函数\( f: U \to \mathbb{C} \)，其中\( U \subset \mathbb{C} \)是[[复平面]]上的一个[[开集]]。如果对于任意 \( z_0 \in U\)，\( f \)在\( z_0 \)处[[复可微]]，即极限
  $$
  \lim_{z \to z_0} \frac{f(z) - f(z_0)}{z - z_0}
  $$
  存在，则称\( f \)在\( U \)上^^全纯^^。
- ### 性质
  全纯函数具有以下重要性质：
	- **无穷可微**：如果函数\( f \)在开集\( U \)上全纯，则\( f \)在\( U \)上无穷次可微。
	  logseq.order-list-type:: number
	- **解析性**：全纯函数在其定义域内是[[解析]]的，即每一点都可以用泰勒级数（或洛朗级数）来局部表示。
	  logseq.order-list-type:: number
	- **[[柯西-黎曼方程]]**：函数\( f = u + iv \)（其中\( u, v \)为实函数）在\( U \)上全纯当且仅当\( u \)和\( v \)满足柯西-黎曼方程：
	  logseq.order-list-type:: number
	   $$
	   \begin{align*}
	   \frac{\partial u}{\partial x} &= \frac{\partial v}{\partial y} \\
	   \frac{\partial u}{\partial y} &= -\frac{\partial v}{\partial x}
	   \end{align*}
	   $$
	- **[[最大模原理]]**：如果\( f \)是非常数的全纯函数，则在其定义域的任意[[紧子集]]上，\( |f(z)| \) 不能取得最大值。
	  logseq.order-list-type:: number
- ### 示例
	- **多项式函数**：所有的多项式函数在整个复平面上都是全纯的。
	- **指数函数**：复指数函数\( e^z \)在整个复平面上全纯。
	- **三角函数**：如\( \sin(z) \)和\( \cos(z) \)在整个复平面上全纯。