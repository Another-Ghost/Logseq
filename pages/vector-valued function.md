alias:: 多元函数

- ### 定义
  
  设 \( f \) 是一个定义在 \( \mathbb{R}^n \) 上的[[函数]]]，其中 \( \mathbb{R}^n \) 是 \( n \) 维[[实数空间]]。则 \( f \) 可表示为：
  $$ f: \mathbb{R}^n \rightarrow \mathbb{R}, \quad f(x_1, x_2, \ldots, x_n) = y $$
  其中，\( x_1, x_2, \ldots, x_n \in \mathbb{R} \) 是[[自变量]]，\( y \in \mathbb{R} \) 是[[因变量]]。
- ### 性质
	- 1. **连续性**：若对于任意 \( \epsilon > 0 \)，存在 \( \delta > 0 \) 使得当 \( ||(x_1, x_2, \ldots, x_n) - (a_1, a_2, \ldots, a_n)|| < \delta \) 时，有 \( |f(x_1, x_2, \ldots, x_n) - f(a_1, a_2, \ldots, a_n)| < \epsilon \)，则 \( f \) 在点 \( (a_1, a_2, \ldots, a_n) \) [[连续]]。
	- 2. **偏导数**：函数 \( f \) 关于 \( x_i \) 的[[偏导数]]定义为：
	   $$ \frac{\partial f}{\partial x_i} = \lim_{h \to 0} \frac{f(x_1, \ldots, x_i + h, \ldots, x_n) - f(x_1, \ldots, x_i, \ldots, x_n)}{h} $$
	- 3. **梯度**：函数 \( f \) 的[[梯度]]定义为：
	   $$ \nabla f = \left( \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2}, \ldots, \frac{\partial f}{\partial x_n} \right) $$
	- 4. **方向导数**：函数 \( f \) 在点 \( (a_1, a_2, \ldots, a_n) \) 沿向量 \( \mathbf{v} \) 的[[方向导数]]定义为：
	  $$ D_{\mathbf{v}} f(a_1, a_2, \ldots, a_n) = \lim_{t \to 0} \frac{f(a_1 + t v_1, a_2 + t v_2, \ldots, a_n + t v_n) - f(a_1, a_2, \ldots, a_n)}{t} $$
	- 5. **可微性**：若存在一个线性映射 \( L: \mathbb{R}^n \rightarrow \mathbb{R} \) 使得：
	   $$ \lim_{\mathbf{h} \to \mathbf{0}} \frac{f(\mathbf{a} + \mathbf{h}) - f(\mathbf{a}) - L(\mathbf{h})}{||\mathbf{h}||} = 0 $$
	  
	   则称 \( f \) 在点 \( \mathbf{a} \) [[可微]]。
- ### 相关定理
	- 1. **[[偏导数连续定理]]**：若函数 \( f \) 在点 \( \mathbf{a} \) 的所有偏导数存在且在 \( \mathbf{a} \) 连续，则 \( f \) 在 \( \mathbf{a} \) [[可微]]。
	- 2. **[[链式法则]]**：若 \( f: \mathbb{R}^n \rightarrow \mathbb{R} \) 且 \( g_i: \mathbb{R}^m \rightarrow \mathbb{R} \)（\( i = 1, 2, \ldots, n \)），则[[复合函数]] \( h = f(g_1, g_2, \ldots, g_n) \) 的导数为：
	   $$ \frac{\partial h}{\partial x_j} = \sum_{i=1}^{n} \frac{\partial f}{\partial y_i
	  } \frac{\partial g_i}{\partial x_j} $$
	- 3. **[[极值定理]]**：若函数 \( f \) 在点 \( \mathbf{a} \) 取得[[局部极值]]且在该点[[可微]]，则 \( \nabla f(\mathbf{a}) = \mathbf{0} \)。
	- 4. **[[拉格朗日乘数法]]**：用于求解在约束条件 \( g(x_1, x_2, \ldots, x_n) = 0 \) 下 \( f(x_1, x_2, \ldots, x_n) \) 的极值问题。如果 \( f \) 和 \( g \) 在点 \( \mathbf{a} \) [[可微]]且 \( \nabla g(\mathbf{a}) \neq \mathbf{0} \)([[梯度]])，则存在 \( \lambda \in \mathbb{R} \) 使得 \( \nabla f(\mathbf{a}) = \lambda \nabla g(\mathbf{a}) \)。
	- 5. **[[隐函数定理]]**：若函数 \( F(x_1, x_2, \ldots, x_n, y) = 0 \) 在点 \( (a_1, a_2, \ldots, a_n, b) \) [[可微]]且 \( \frac{\partial F}{\partial y} \neq 0 \)，则存在一个[[局部函数]] \( y = f(x_1, x_2, \ldots, x_n) \) 使得 \( F(x_1, x_2, \ldots, x_n, f(x_1, x_2, \ldots, x_n)) = 0 \)。