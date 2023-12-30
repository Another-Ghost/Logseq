alias:: 酉矩阵

- ## 定义
  一个 \( n \times n \) 的[[复数矩阵]] \(\boldsymbol  U \) 被称为[[酉矩阵]]，如果它满足以下条件：
  $$ \boldsymbol U^*\boldsymbol U = \boldsymbol {UU}^* =\boldsymbol  I $$
  其中，\(\boldsymbol  U^* \) 表示 \(\boldsymbol  U \) 的[[共轭转置]]（也称[[伴随矩阵]]），\(\boldsymbol  I \) 是 \( n \times n \) 的单位矩阵。
- ### 相关定理
	- **列向量和行向量构成正交基**：
	  logseq.order-list-type:: number
	   酉矩阵的列向量和行向量构成复数向量空间的[[正交归一基]]。这意味着这些向量两两正交，并且每个向量的范数（长度）都是1。
	- **[[保范性]]**：
	  logseq.order-list-type:: number
	   酉矩阵保持[[向量的范数]]不变。对于任意向量 \( \mathbf{v} \)，有 \( \| U\mathbf{v} \| = \| \mathbf{v} \| \)。
	- **可逆性**：
	  logseq.order-list-type:: number
	   每个酉矩阵都是[可逆]([[可逆矩阵]])的，且其逆矩阵就是它的共轭转置：\( U^{-1} = U^* \)。
	- **特征值的模为 1**：
	  logseq.order-list-type:: number
	   酉矩阵的所有[[特征值的模]]（绝对值）都是 $1$ 。这意味着[[特征值]]都位于[[复数平面]]的[[单位圆]]上。
	- **[[谱定理]]**：
	  logseq.order-list-type:: number
	   对于每个酉矩阵，都存在一个酉矩阵 \( V \)，使得 \( U \) 可以被对角化为 \( VDV^{-1} \) 或 \( VDV^* \)，其中 \( D \) 是一个对角矩阵，其对角线上的元素是 \( U \) 的特征值。
	- **乘积和逆的酉性**：
	  logseq.order-list-type:: number
	   如果 \( U \) 和 \( V \) 是酉矩阵，那么它们的[乘积]([[矩阵乘积]]) \( UV \) 也是酉的，且 \( U \) 的[逆]([[逆矩阵]]) \( U^{-1} \)（或 \( U^* \)）也是酉的。