alias:: 海森矩阵

- ### 定义
  对于一个定义在 \( \mathbb{R}^n \) 中并且在点 \( \mathbf{x} \) 处[[二阶可微]]的函数 \( f: \mathbb{R}^n \rightarrow \mathbb{R} \)，其海森矩阵 \( H(f) \) 在 \( \mathbf{x} \) 处定义为一个 \( n \times n \) 的矩阵，其元素由 \( f \) 的[[二阶偏导数]]组成：
  $$ H(f)(\mathbf{x}) = \begin{bmatrix}
  \frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
  \frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
  \vdots & \vdots & \ddots & \vdots \\
  \frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2}
  \end{bmatrix} $$
- ### 性质
  
  1. **对称性**：海森矩阵是对称的，即 \( \frac{\partial^2 f}{\partial x_i \partial x_j} = \frac{\partial^2 f}{\partial x_j \partial x_i} \)。
  
  2. **判定极值**：若函数 \( f \) 在点 \( \mathbf{x} \) 处的一阶偏导数为零（即 \( \nabla f(\mathbf{x}) = \mathbf{0} \)），则海森矩阵的[[特征值]]可以用来判定该点的[[极值]]类型：
	- 如果 \( H(f)(\mathbf{x}) \) 的所有特征值都是正的，那么 \( f(\mathbf{x}) \) 是[[局部极小值]]。
	- 如果 \( H(f)(\mathbf{x}) \) 的所有特征值都是负的，那么 \( f(\mathbf{x}) \) 是[[局部极大值
	- ]]。
	- 如果 \( H(f)(\mathbf{x}) \) 的特征值中既有正数也有负数，那么 \( \mathbf{x} \) 是[[鞍点]]。
- 3. **[[凹凸性]]判定**：如果对于定义域中所有点 \( \mathbf{x} \)，海森矩阵 \( H(f)(\mathbf{x}) \) 是[[正定]]的（所有特征值都是正的），那么 \( f \) 是凸函数；如果是负定的（所有特征值都是负的），那么 \( f \) 是凹函数。
  
  海森矩阵在优化问题、经济学和工程学中的多个应用中发挥着关键作用，特别是在涉及二阶导数信息的问题中。