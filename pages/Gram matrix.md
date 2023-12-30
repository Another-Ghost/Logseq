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
- # Gram矩阵的性质
	- **[[对称性]]**：由于内积的共轭对称性，Gram 矩阵是对称的。
	  logseq.order-list-type:: number
	- **[[半正定]]**：对于任何向量 \( \mathbf{x} \)，都有 \( \mathbf{x}^T G \mathbf{x} \geq 0 \)。**
	  logseq.order-list-type:: number
	- **[[线性独立性]]**：如果一组向量 \( \mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_n \) 在某个内积空间中是[[线性独立]]的，那么由这些向量构成的Gram矩阵是[[非奇异]]的。
	  logseq.order-list-type:: number
	  反之，如果这组向量线性相关，那么它们的Gram矩阵是奇异的。
- > 通过分析Gram矩阵，可以获取向量集合的[[线性独立性]]、[[正交性]]和其他重要属性。
-