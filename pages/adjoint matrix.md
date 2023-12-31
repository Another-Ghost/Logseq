alias:: 伴随矩阵

- ## 定义
  对于任何 \( m \times n \) 的[[复数矩阵]] \( A \)，其[[伴随矩阵]] \( A^* \) 是一个 \( n \times m \) 的矩阵，满足：
  $$ A^* = \overline{A}^T $$
  其中，\( \overline{A} \) 表示矩阵 \( A \) 的[[共轭]]，即将 \( A \) 中的每个元素取共轭，而 \( T \) 表示转置操作，即将矩阵沿对角线翻转。
- ### 相关定理和性质
	- 1. **线性**：
	   对于任意两个矩阵 \( A \) 和 \( B \) 以及任意标量 \( c \)，都有：
	   $$ (A + B)^* = A^* + B^* $$
	   $$ (cA)^* = \overline{c}A^* $$
	- 2. **乘积的伴随**：
	   对于任意两个矩阵 \( A \) 和 \( B \)，伴随矩阵的乘积满足：
	   $$ (AB)^* = B^*A^* $$
	   这表明伴随操作是反交换的。
	- 3. **[[自伴随矩阵]]**：
	   如果一个矩阵与其伴随矩阵相等，即 \( A = A^* \)，则称该矩阵为自伴随的。
		- 对于[[实数矩阵]]来说，这意味着矩阵是[对称]([[对称矩阵]])的；
		- 对于[[复数矩阵]]来说，这意味着矩阵是[[Hermite 矩阵]]。
	- 4. **范数**：
	   对于任意矩阵 \( A \)，矩阵和其伴随矩阵的乘积 \( A^*A \) 总是[[半正定]]的。这种乘积的[[迹]]等于 \( A \) 的[[Frobenius 范数]]的平方。
	- 5. **[[逆矩阵]]的伴随**：
	   如果矩阵 \( A \) 是可逆的，那么其逆矩阵的伴随等于伴随矩阵的逆：
	   $$ (A^{-1})^* = (A^*)^{-1}$$
-
-