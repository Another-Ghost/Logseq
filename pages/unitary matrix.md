## 定义
一个 \( n \times n \) 的[[复数矩阵]] \(\boldsymbol  U \) 被称为[[酉矩阵]]，如果它满足以下条件：
$$ \boldsymbol U^*\boldsymbol U = \boldsymbol {UU}^* =\boldsymbol  I $$
其中，\(\boldsymbol  U^* \) 表示 \(\boldsymbol  U \) 的[[共轭转置]]（也称[[伴随矩阵]]），\(\boldsymbol  I \) 是 \( n \times n \) 的单位矩阵。
- ### 相关定理
	- **列向量和行向量构成正交基**：
	  logseq.order-list-type:: number
	   酉矩阵的列向量和行向量构成复数向量空间的正交归一基。这意味着这些向量两两正交，并且每个向量的范数（长度）都是1。
	- **保范性（Preserves Norm）**：
	  logseq.order-list-type:: number
	   酉矩阵保持向量的范数不变。对于任意向量 \( \mathbf{v} \)，有 \( \| U\mathbf{v} \| = \| \mathbf{v} \| \)。
	- logseq.order-list-type:: number
	  3. **可逆性**：
	   每个酉矩阵都是可逆的，且其逆矩阵就是它的共轭转置：\( U^{-1} = U^* \)。
	- logseq.order-list-type:: number
	  4. **特征值的模为1**：
	   酉矩阵的所有特征值的模（绝对值）都是1。这意味着特征值都位于复数平面的单位圆上。
	- logseq.order-list-type:: number
	  5. **谱定理（Spectral Theorem）**：
	   对于每个酉矩阵，都存在一个酉矩阵 \( V \)，使得 \( U \) 可以被对角化为 \( VDV^{-1} \) 或 \( VDV^* \)，其中 \( D \) 是一个对角矩阵，其对角线上的元素是 \( U \) 的特征值。
	- logseq.order-list-type:: number
	  6. **乘积和逆的酉性**：
	   如果 \( U \) 和 \( V \) 是酉矩阵，那么它们的乘积 \( UV \) 也是酉的，且 \( U \) 的逆 \( U^{-1} \)（或 \( U^* \)）也是酉的。