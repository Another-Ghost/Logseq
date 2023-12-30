alias:: 正交分解定理

- ### 定义
  设 \(V\) 是一个[[内积空间]]，\(W\) 是 \(V\) 的一个[[子空间]]。[[正交分解定理]]]指出，\(V\) 中的每一个向量 \(\boldsymbol{v}\) 都可以唯一地表示为两个向量 \(\boldsymbol{w}\) 和 \(\boldsymbol{w}^\perp\) 的和，其中 \(\boldsymbol{w}\) 属于 \(\boldsymbol{W}\)，而 \(\boldsymbol{w}^\perp\) 属于 \(W\) 的正交补空间 \(W^\perp\)。
  
  数学表达为：
  \[ \boldsymbol{v} = \boldsymbol{w} + \boldsymbol{w}^\perp \]
  其中 \(\boldsymbol{w} \in \boldsymbol{W}\) 且 \(\boldsymbol{w}^\perp \in \boldsymbol{W}^\perp\)，并且 \(\boldsymbol{w}\) 和 \(\boldsymbol{w}^\perp\) 正交，即：
  \[ \boldsymbol{w} \cdot \boldsymbol{w}^\perp = 0 \]
- ### 性质
  1. **唯一性**：对于 \(\boldsymbol{V}\) 中的任意向量 \(\boldsymbol{v}\)，其在 \(\boldsymbol{W}\) 和 \(\boldsymbol{W}^\perp\) 中的分解是唯一的。
  2. **最小距离**：分解中的 \(\boldsymbol{w}\) 是 \(\boldsymbol{W}\) 中离 \(\boldsymbol{v}\) 最近的点。这是最小二乘问题中的一个关键概念。
  3. **正交投影**：分解中的 \(\boldsymbol{w}\) 可以通过将 \(\boldsymbol{v}\) 正交投影到 \(\boldsymbol{W}\) 上得到。
- ### 应用
- **最小二乘法**：在数据拟合和统计中，用于找到一组数据点的最佳拟合线或平面。
- **信号处理**：在去噪或信号分离中，可以用来分离出噪声和信号的不同成分。
- **数据压缩**：在数据压缩技术中，如主成分分析（PCA），用于降维和特征提取。
  
  正交分解定理提供了一种强大的工具，用于理解和操作子空间及其正交补空间中的向量。