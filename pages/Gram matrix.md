alias:: Gram 矩阵, 格拉姆矩阵

- 假设你有一组向量 \( \mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_n \)，这些向量属于某个内积空间。这组向量的Gram矩阵 \( G \) 定义为：
- \[ G = 
  \begin{bmatrix}
  \langle \mathbf{v}_1, \mathbf{v}_1 \rangle & \langle \mathbf{v}_1, \mathbf{v}_2 \rangle & \cdots & \langle \mathbf{v}_1, \mathbf{v}_n \rangle \\
  \langle \mathbf{v}_2, \mathbf{v}_1 \rangle & \langle \mathbf{v}_2, \mathbf{v}_2 \rangle & \cdots & \langle \mathbf{v}_2, \mathbf{v}_n \rangle \\
  \vdots & \vdots & \ddots & \vdots \\
  \langle \mathbf{v}_n, \mathbf{v}_1 \rangle & \langle \mathbf{v}_n, \mathbf{v}_2 \rangle & \cdots & \langle \mathbf{v}_n, \mathbf{v}_n \rangle
  \end{bmatrix}
  \]
- 其中，\( \langle \mathbf{v}_i, \mathbf{v}_j \rangle \) 表示向量 \( \mathbf{v}_i \) 和 \( \mathbf{v}_j \) 的内积。
- Gram矩阵的性质：
  1. **对称性（Symmetric）**：由于内积的共轭对称性，Gram矩阵是对称的。
  2. **半正定（Positive Semi-definite）**：对于任何向量 \( \mathbf{x} \)，都有 \( \mathbf{x}^T G \mathbf{x} \geq 0 \)。
- Gram矩阵在多个领域都非常有用，例如在数值线性代数、统计学、机器学习和信号处理等领域。通过分析Gram矩阵，可以获取向量集合的线性独立性、正交性和其他重要属性。例如，在主成分分析（PCA）和线性判别分析（LDA）等方法中，Gram矩阵提供了关于数据集几何结构的重要信息。