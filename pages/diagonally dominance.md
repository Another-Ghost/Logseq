alias:: 对角占优, diagonally dominant

- 对角占优（Diagonal Dominance）是线性代数中矩阵理论的一个重要概念。一个矩阵被称为对角占优的，如果它的每个对角线元素（即行或列的主元素）在绝对值上大于该行或该列的其他元素的绝对值之和。更具体地，这个概念可以分为行对角占优和列对角占优：
	- **行对角占优**：对于一个 \( n \times n \) 矩阵 \( A = [a_{ij}] \)，如果对于所有的 \( i \)（\( 1 \leq i \leq n \)），都有
	  logseq.order-list-type:: number
	     $$|a_{ii}| > \sum_{\substack{j=1 \\ j \neq i}}^{n} |a_{ij}|$$
	     那么矩阵 \( A \) 被称为行对角占优。
	- **列对角占优**：同样地，如果对于所有的 \( j \)（\( 1 \leq j \leq n \)），都有
	  logseq.order-list-type:: number
	    $$|a_{jj}| > \sum_{\substack{i=1 \\ i \neq j}}^{n} |a_{ij}|$$
	     那么矩阵 \( A \) 被称为列对角占优。
- ### 重要性和应用
  对角占优是一个非常重要的性质，因为它与矩阵的多种性质相关，例如：
	- **可逆性**：一个严格对角占优的矩阵是非奇异的，即可逆的。
	- **数值稳定性**：对角占优矩阵在数值计算中通常更稳定。
	- **收敛性**：在迭代方法中求解线性系统时，对角占优可以保证一定的收敛性质。
- 在工程和科学领域，对角占优的概念在分析和设计算法，特别是在求解线性方程组和稀疏矩阵问题时非常有用。例如，在电气工程和计算流体动力学中，对角占优性质被用来确保数值方法的有效性和稳定性。