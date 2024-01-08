alias:: 范数, 模

- ### 定义
  
  范数是一个[[函数]] \( \|\cdot\|: V \rightarrow \mathbb{R} \)，其中 \( V \) 是一个[[向量空间]]，满足以下性质：
  
  1. **非负性**：对于所有 \( \mathbf{v} \in V \)，有 \( \|\mathbf{v}\| \geq 0 \)，且 \( \|\mathbf{v}\| = 0 \) 当且仅当 \( \mathbf{v} = \mathbf{0} \)。
  2. **齐次性**：对于任何标量 \( \alpha \) 和 \( \mathbf{v} \in V \)，有 \( \|\alpha \mathbf{v}\| = |\alpha| \|\mathbf{v}\| \)。
  3. **三角不等式**：对于所有 \( \mathbf{u}, \mathbf{v} \in V \)，有 \( \|\mathbf{u} + \mathbf{v}\| \leq \|\mathbf{u}\| + \|\mathbf{v}\| \)。
- ### 常见类型的范数
  
  1. **[[欧几里得范数]]（\( L^2 \) 范数）**：定义为 \( \|\mathbf{v}\|_2 = \sqrt{v_1^2 + v_2^2 + \cdots + v_n^2} \)。这是最常见的范数，表示向量的几何长度。
  
  2. **[[曼哈顿范数]]（\( L^1 \) 范数）**：定义为 \( \|\mathbf{v}\|_1 = |v_1| + |v_2| + \cdots + |v_n| \)。这表示向量的分量绝对值之和。
  
  3. **[[最大值范数]]（\( L^\infty \) 范数）**：定义为 \( \|\mathbf{v}\|_\infty = \max(|v_1|, |v_2|, \ldots, |v_n|) \)。这是向量的所有分量绝对值中的最大值。
  
  4. **[[p-范数]]**：对于 \( 1 \leq p < \infty \)，\( p \)-范数定义为 \( \|\mathbf{v}\|_p = (|v_1|^p + |v_2|^p + \cdots + |v_n|^p)^{1/p} \)。
- ## [[向量范数]]
- ## [[矩阵范数]]