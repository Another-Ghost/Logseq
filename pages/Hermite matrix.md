alias:: 自伴随矩阵, self-adjoint matrix

- ### 定义
  一个 \( n \times n \) [[复数矩阵]] \(\boldsymbol{A}\) 被称为[[Hermite 矩阵]]，如果它等于自己的[[共轭转置]]，即：
  $$ \boldsymbol{A} = \boldsymbol{A}^* $$
  其中，\(\boldsymbol{A}^*\) 是 \(\boldsymbol{A}\) 的共轭转置。
- ### 性质
	- 1. **对称性**：
	   Hermite 矩阵是[对称]()的，即 \(\boldsymbol{A}_{ij} = \overline{\boldsymbol{A}_{ji}}\)，这里 \(\overline{\boldsymbol{A}_{ji}}\) 表示 \(\boldsymbol{A}_{ji}\) 的共轭。
	- 2. **实数对角线**：
	   Hermite矩阵的对角元素都是实数。
	- 3. **特征值是实数**：
	   Hermite矩阵的所有特征值都是实数。
	- 4. **酉对角化**：
	   每个Hermite矩阵都可以被一个酉矩阵对角化。这意味着存在一个酉矩阵 \(\boldsymbol{U}\) 和一个实数对角矩阵 \(\boldsymbol{D}\)，使得 \(\boldsymbol{A} = \boldsymbol{U}\boldsymbol{D}\boldsymbol{U}^*\)。
- ### 相关定理
  1. **谱定理（Spectral Theorem）**：
   对于任何Hermite矩阵 \(\boldsymbol{A}\)，都存在一个酉矩阵 \(\boldsymbol{U}\)，使得 \(\boldsymbol{A}\) 可以被对角化为 \(\boldsymbol{U}\boldsymbol{D}\boldsymbol{U}^*\)，其中 \(\boldsymbol{D}\) 是对角矩阵，且对角线上的元素是 \(\boldsymbol{A}\) 的特征值。
  
  2. **正定性**：
   如果对于所有非零向量 \(\boldsymbol{v}\)，都有 \(\boldsymbol{v}^*\boldsymbol{A}\boldsymbol{v} > 0\)，则Hermite矩阵 \(\boldsymbol{A}\) 是正定的。
  
  Hermite矩阵在量子力学、信号处理和多种数学问题中扮演着关键角色，特别是在涉及复数矩阵的情况下。这些性质和定理使得Hermite矩阵成为描述物理系统和进行复数矩阵分析的重要工具。