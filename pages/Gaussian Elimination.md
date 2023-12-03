alias:: 高斯消元法

- [[高斯消元法]]是一种用于求解[[线性方程组]]的算法。它通过行变换将线性方程组的系数矩阵转换成行阶梯形矩阵，从而简化求解过程。以下是高斯消元法的基本步骤：
	- *准备阶段* 
	  logseq.order-list-type:: number
		- 将线性方程组写成[[增广矩阵]]形式。增广矩阵是[[系数矩阵]]和[[常数项向量组]]合在一起的矩阵。
		  logseq.order-list-type:: number
	- [[前向消元]]：
	  logseq.order-list-type:: number
		- 选取一个[[主元]]（一般是当前[[列]]的**最上面的非零元素**）。
		- 使用[[行变换]]使得[[主元]]所在列下方的所有元素变为 0 。这通常通过**将主元所在行的倍数加到下方的行上**来实现。
		- 对每个主元**重复**此过程，直到所有主元下方的元素都变为 0 。
	- 检查[[解]]的存在性和唯一性：
	  logseq.order-list-type:: number
		- 如果在某个阶段，某行除了最后一个元素外都是0，但最后一个元素（即常数项）不为0，则 *方程组无解* 。
		- 如果最后得到的行阶梯形矩阵中有**至少一行全为0**，则 *方程组有无限多解* 。
	- [[回代]]：
	  logseq.order-list-type:: number
		- 从最后一个[[主元]]开始，利用已经求得的[[解]]来解出其他[[变量]]。
		  逐步向上进行，每次解出一个变量。
	- 解的提取：
	  logseq.order-list-type:: number
		- 从上到下提取每个变量的解。
- 高斯消元法可能会遇到[[数值稳定性]]问题，尤其是当[[主元]]很小的时候。
  为了避免这种问题，通常会使用[[部分选主元]]策略，即在每一步选取**当前列绝对值最大的元素**作为[[主元]]。这种方法可以提高算法的[[数值稳定性]]。
- # 具体步骤
	- ## [[消元]]
		- 记 
		  $$\boldsymbol A^{(1)}=\boldsymbol A=\left(a_{ij}^{(1)}\right)_{n\times n},\boldsymbol{b}^{(1)}=\boldsymbol{b}=\left(\begin{matrix}b_1^{(1)}\\\vdots\\b_n^{(1)}\end{matrix}\right)$$
		- 第 $1$ 步: 设 $a_{11}^{(1)}\neq0$, [[计算因子]] 
		  $$l_{i1}=\frac{a_{i1}^{(1)}}{a_{11}^{(1)}}\quad(i=2,...,n)$$ 
		  [[将增广矩阵]] 第 i 行
		  $$\{a_{i1},\cdots,a_{in}\} - l_{i1} \{a_{11}\cdots,a_{1n}\}$$
		  得到
		  \begin{pmatrix}
		   a & \begin{matrix} 0 & 0 & \dots & 0 \end{matrix} & b^{(1)}_1\\
		   \begin{matrix} 0 \\ 0 \\ \vdots \\[1ex] 0 \end{matrix} & \huge{\boldsymbol A^{(2)}} & \huge{\boldsymbol b^{(2)}}
		  \end{pmatrix}
		  其中
		  $$\left \{\begin{aligned} 
		  a^{(2)}_{ij}= a^{(1)}_{ij}-l_{i1}a^{(1)}_{1j} \\ 
		  b^{(2)}_{i}= b^{(1)}_{i}-l_{i1}b^{(1)}_{1}
		  \end{aligned} \right.$$
		- 第 $k$ 步: 设 $a_{kk}^{(k)}\neq0$ , [[计算因子]] 
		  $$l_{ik}=\frac{a_{ik}^{(k)}}{a_{kk}^{(k)}}\quad(i=k+1,...,n)$$ 
		  且计算
		  $$\left \{\begin{aligned} 
		  a^{(k+1)}_{ij}= a^{(k)}_{ij}-l_{ik}a^{(k)}_{kj} \\ 
		  b^{(k+1)}_{i}= b^{(k)}_{i}-l_{ik}b^{(k)}_{k}
		  \end{aligned} \right.$$
		- 共进行 $n-1$ 步
		  $$\left(\begin{array}{cccc}
		  a_{11}^{(1)} & a_{12}^{(1)} & \ldots & a_{1 n}^{(1)} \\
		  & a_{22}^{(2)} & \ldots & a_{2 n}^{(2)} \\
		  & & \ldots & \vdots \\
		  & & & a_{n n}^{(n)}
		  \end{array}\right)
		  \left(\begin{array}{c}
		  x_{1} \\
		  x_{2} \\
		  \vdots \\
		  x_{n}
		  \end{array}\right)=
		  \left(\begin{array}{c}
		  b_{1}^{(1)} \\
		  b_{2}^{(2)} \\
		  \vdots \\
		  b_{n}^{(n)}
		  \end{array}\right)$$
	- ## [[回代]]
		- $$x_n=\frac{b_n^{(n)}}{a_{nn}^{(n)}}$$
		- $$
		  x_i=\frac{b_i^{(i)}-\sum_{j=i+1}^n a_{ij}^{(i)}x_j}{a_{ii}^{(i)}} \quad(i=n-1,...,1)
		  $$
- # Theorem
	- 如果 $\boldsymbol A$ 为 $n$ 阶[[非奇异矩阵]]，则可通过[[高斯消去法]](及交换两行的[[初等行变换]]) 将方程组化为 *三角形方程组* 。
	  logseq.order-list-type:: number
		- ## Corollary
			- 约化的[[主元素]] $a_{ii}^{(i)}\neq0\left(i=1,2,\cdots,k\right)$ 的 充要条件 是矩阵 $\boldsymbol A$ 的[[顺序主子式]] $D_i\neq0\left(i=1,2,\cdots,k\right)$ 。
			  logseq.order-list-type:: number
			- 如果A的[[顺序主子式]]$D_k\neq0\quad(k=1,2,\cdots,n-1)$ 则 
			  logseq.order-list-type:: number
			  $$
			  \begin{cases}a_{11}^{(1)}=D_1\\a_{kk}^{(k)}=D_k/D_{k-1}&\end{cases}
			  $$
			- 定理 若 $A$ 的所有[[顺序主子式]]均不为 $0$ ，则 高斯消元 无需[[交换行]]即可完成，且[[线性方程组的解]]**唯一**。
			  logseq.order-list-type:: number
-