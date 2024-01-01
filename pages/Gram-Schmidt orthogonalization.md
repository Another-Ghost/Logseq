alias:: 施密特正交化

- [[施密特正交化]]是从一组[[线性独立]]的向量出发，逐步构造出一组[[正交]]向量的方法。
  这个过程基于一个简单的想法：从给定的向量集合中减去它们在已生成的正交向量上的[[投影]]，从而产生一个新的正交向量。
- ### 步骤
  1. **开始**：从一组线性独立的向量 \(\{ \boldsymbol{v}_1, \boldsymbol{v}_2, \ldots, \boldsymbol{v}_n \}\) 开始。
  
  2. **第一个正交向量**：第一个正交向量 \(\boldsymbol{u}_1\) 就是 \(\boldsymbol{v}_1\)，因为没有其他向量与其比较正交性。
  
  3. **逐个构造**：对于 \( k = 2, 3, \ldots, n \)，按以下方式构造 \(\boldsymbol{u}_k\)：
	- 首先，取 \(\boldsymbol{v}_k\)。
	- 然后，从 \(\boldsymbol{v}_k\) 中减去其在之前所有 \(\boldsymbol{u}_j\) (\(j < k\)) 上的投影，即：
	  $$\boldsymbol{u}_k = \boldsymbol{v}_k - \sum_{j=1}^{k-1} \text{proj}_{\boldsymbol{u}_j}(\boldsymbol{v}_k)$$
	- 其中，\(\text{proj}_{\boldsymbol{u}_j}(\boldsymbol{v}_k)\) 是 \(\boldsymbol{v}_k\) 在 \(\boldsymbol{u}_j\) 上的投影，计算为：
	  $$ \text{proj}_{\boldsymbol{u}_j}(\boldsymbol{v}_k) = \frac{\langle \boldsymbol{v}_k, \boldsymbol{u}_j \rangle}{\langle \boldsymbol{u}_j, \boldsymbol{u}_j \rangle} \boldsymbol{u}_j$$
	  
	  4. **结果**：经过上述步骤，我们得到一组正交向量 \(\{ \boldsymbol{u}_1, \boldsymbol{u}_2, \ldots, \boldsymbol{u}_n \}\)。
- ### 直观解释
  直观上，施密特正交化的每一步都在确保新生成的向量与之前生成的所有向量正交。通过减去在已有正交向量上的投影，新向量被“校正”为与已有正交向量集合正交。
- ### 应用
  这种方法在构建正交基（例如，在求解线性方程组、数据降维、或在计算机图形学中）时非常有用。正交基简化了很多数学计算，因为在正交基下，很多问题都有更简单直观的解释。