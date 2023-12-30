alias:: Gram 矩阵, 格拉姆矩阵

- 假设你有一组向量 \( \mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_n \)，这些向量属于某个[[内积空间]]。这组向量的[[Gram 矩阵]] \(\boldsymbol G \) 定义为：
- $$\boldsymbol G = 
  \begin{bmatrix}
  \langle \mathbf{v}_1, \mathbf{v}_1 \rangle & \langle \mathbf{v}_1, \mathbf{v}_2 \rangle & \cdots & \langle \mathbf{v}_1, \mathbf{v}_n \rangle \\
  \langle \mathbf{v}_2, \mathbf{v}_1 \rangle & \langle \mathbf{v}_2, \mathbf{v}_2 \rangle & \cdots & \langle \mathbf{v}_2, \mathbf{v}_n \rangle \\
  \vdots & \vdots & \ddots & \vdots \\
  \langle \mathbf{v}_n, \mathbf{v}_1 \rangle & \langle \mathbf{v}_n, \mathbf{v}_2 \rangle & \cdots & \langle \mathbf{v}_n, \mathbf{v}_n \rangle
  \end{bmatrix}
  $$
- 其中，\( \langle \mathbf{v}_i, \mathbf{v}_j \rangle \) 表示向量 \( \mathbf{v}_i \) 和 \( \mathbf{v}_j \) 的内积。
- ## Gram矩阵的性质
	- **[[对称性]]**：由于内积的共轭对称性，Gram 矩阵是对称的。
	  logseq.order-list-type:: number
	- **[[半正定]]**：对于任何向量 \( \mathbf{x} \)，都有 \( \mathbf{x}^T G \mathbf{x} \geq 0 \)。**
	  logseq.order-list-type:: number
	- **[[线性独立性]]**：如果一组向量 \( \mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_n \) 在某个内积空间中是[[线性独立]]的，那么由这些向量构成的Gram矩阵是[[非奇异]]的。
	  logseq.order-list-type:: number
	  反之，如果这组向量线性相关，那么它们的Gram矩阵是奇异的。
	- **[[秩]]**：Gram 矩阵的秩等于原向量集合的秩。也就是说，它反映了原向量集合的线性独立向量的最大数量。
	  logseq.order-list-type:: number
	- **谱定理**：由于Gram矩阵是实对称矩阵（或在复数域上是[[Hermite 矩阵]]），根据[[谱定理]]，它可以被[[对角化]]。这意味着存在一个[[正交矩阵]]（或[[酉矩阵]]）矩阵 \( Q \) 和一个对角矩阵 \( D \)，使得 \( G = QDQ^T \)（或在复数域上为 \( G = QDQ^* \)），其中 \( D \) 的对角线元素是 \( G \) 的特征值。
	  logseq.order-list-type:: number
	- 5. **正交分解定理**：对于任何向量 \( \mathbf{u} \) 和Gram矩阵对应的向量空间，都存在唯一的分解，使得 \( \mathbf{u} \) 可以写成空间中向量的线性组合和垂直于该空间的部分之和。
-
-