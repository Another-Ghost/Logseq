alias:: 最小二乘法, 曲线拟合的最小二乘法, 最小二乘拟合, 最小二乘逼近

- 在函数的[[最佳平方逼近]]中 $f(x)\in C[a,b]$, 如果 $f(x)$ 只在一组[[离散点集]] {$x_i,i=0$, $1,\cdots,m\}$ 上给出，这就是 $m+1$ 个数据 $\left\{(x_i,y_i),i=0,1,\cdots,m\right\}$的[[曲线拟合]]。这里 $y_i=f(x_i)(i=0,1,\cdots,m)$ , 要求一个函数 $y=S^*(x)$ 与所给数据 $\{(x_i, y_i), i=0, 1,\cdots,m\}$ 拟合，若记误差 $\delta_i=\mathcal{S}^*(x_i)-y_i(i=0,1,\cdotp\cdotp\cdotp,m), \boldsymbol \delta=(\delta_0,\delta_1,\cdots,\delta_m)^\mathrm{T},$
  设 $\varphi_0(x), \varphi_1(x),\cdotp\cdotp\cdotp,\varphi_n(x)$ 是 $C[a,b]$ 上[[线性无关函数族]]，$\varphi(x)$ 是在 $\varphi=\operatorname{span}\{\varphi_0(x),\varphi_1(x),\cdotp\cdotp\cdotp,\varphi_n(x)\}$ 中找一函数 $S^*(x)$, 使[[误差平方和]]
  $$
  \parallel\boldsymbol \delta\parallel_2^2=\sum_{i=0}^m\delta_i^2=\sum_{i=0}^m\begin{bmatrix}S^*(x_i)-y_i\end{bmatrix}^2 \tag{1}
  $$
  达到**极小**，这里
  $$
  \begin{aligned}S(x)&=a_0\varphi_0(x)+a_1\varphi_1(x)+\cdots+a_n\varphi_n(x)\quad(n<m).\end{aligned} \tag{2}
  $$
  这就是一般的[[最小二乘逼近]]，用几何语言说，就称为[[曲线拟合的最小二乘法]].
	- 若 $\varphi_k(x)$ 是 $k$ 次多项式，$S(x)$ 就是 $n$ 次[[多项式]].
- ### 加权平方和
  为了使问题的提法更有一般性，通常在最小二乘法中$\|\delta\|_{\frac22}^2$都考虑为加[[权函数]]  $\omega(x)$，表示不同点$(x_i,f(x_i))$处的数据比重不同：
  $$
  \parallel\boldsymbol \delta\parallel_2^2=\sum_{i=0}^m\omega(x_i)[S(x_i)-f(x_i)]^2.
  $$
- ### 最小二乘法转化为多元函数求极值问题
  求一函数 $y=S^*(x)$ , 使上式取得最小，它转化为求多元函数
  $$
  I(a_0,a_1,\cdots,a_n)=\sum_{i=0}^m\omega(x_i)\Big[\sum_{j=0}^na_j\varphi_j(x_i)-f(x_i)\Big]^2.
  $$
  的[[极小点]] $(a_0^*,a_1^*,...,a_n^*)$ 的问题.
  由[[多元函数求极值的必要条件]]，有
  $$
  \frac{\partial I}{\partial a_k}=2\sum_{i=0}^m\omega(x_i)\Big[\sum_{j=0}^na_i\varphi_j(x_i)-f(x_i)\Big]\varphi_k(x_i)=0\:,\quad k=0,1,\cdots,n.
  $$
- ### 法方程
  collapsed:: true
  引入内积
  $$
  (\varphi_j,\varphi_k)=\sum_{i=0}^m\omega(x_i)\varphi_j(x_i)\varphi_k(x_i)\:,
  $$
  $$
  (f,\varphi_k)=\sum_{i=0}^m\omega(x_i)f(x_i)\varphi_k(x_i)\equiv d_k,\quad k=0,1,\cdots,n,
  $$
  上式可改写为[[线性方程组]]
  $$
  \sum_{j=0}^n{(\varphi_k,\varphi_j)a_j}=d_k,\quad k=0,1,\cdotp\cdotp\cdotp,n.
  $$
  称为[[法方程]]。可将其写成矩阵形式
  $$\boldsymbol {Ga}=\boldsymbol d,$$
  其中
  $$
  G = \begin{bmatrix}
  (\phi_0, \phi_0) & (\phi_0, \phi_1) & \cdots & (\phi_0, \phi_n) \\
  (\phi_1, \phi_0) & (\phi_1, \phi_1) & \cdots & (\phi_1, \phi_n) \\
  \vdots & \vdots & \ddots & \vdots \\
  (\phi_n, \phi_0) & (\phi_n, \phi_1) & \cdots & (\phi_n, \phi_n) \\
  \end{bmatrix}
  $$
	- >连续型内积：$(f,g)=\sum_{i=1}^N\omega(x_i)f(x_i)g(x_i)$
	  离散型内积：$\int_a^b\rho(x)f(x)g(x)dx$
	- >要使法方程有唯一解$a_0,a_1,\cdots,a_n$,就要求矩阵$G$非奇异，必须指出，$\varphi_0(x)$, $\varphi_1(x),...,\varphi_n(x)$在$[a,b]$上线性无关**不能**推出矩阵$G$非奇异.例如，令$\varphi_0(x)=\sin x,\varphi_1(x)=$ $\sin2x,x\in[0,2\pi]$,显然$\{\varphi_0(x),\varphi_1(x)\}$在$[0,2\pi]$上线性无关，但若取点$x_k=k\pi,k=0,1,2$ $(n=1,m=2)$,那么有$\varphi_0(x_k)=\varphi_1(x_k)=0,k=0,1,2$,由此得出
	  $$G = \begin{pmatrix}
	  \langle \phi_0, \phi_0 \rangle & \langle \phi_0, \phi_1 \rangle \\
	  \langle \phi_1, \phi_0 \rangle & \langle \phi_1, \phi_1 \rangle
	  \end{pmatrix} = 0.$$
	  所以为保证方程组的系数矩阵$G$非奇异，必须加上另外的条件.
- ### 哈尔条件
  设 $\varphi_0(x),\varphi_1(x),...,\varphi_n(x)\in\mathbb{C}[a,b]$ 的任意线性组合在点集 $\{x_i, i=0,1,\cdots,m\}(m\geqslant n)$ 上至多只有 $n$ 个不同的[[零点]]，则称 $\varphi_0(x),\varphi_1(x),\cdotp\cdotp\cdotp,\varphi_n(x)$ 在点集 $\{x_i,i=0$, $1,\cdotp\cdotp\cdotp,m\}$上满足[[哈尔条件]]。
	- 显然 $1,x,\cdots,x^n$ 在任意 $m{(m{\geqslant}n)}$ 个点上满足哈尔条件.
- ### 最小二乘解
  可以证明，如果$\varphi_0(x),\varphi_1(x),...,\varphi_n(x)\in C[a,b]$在 $\{x_i\}_0^m$ 上满足[[Haar 条件]]，则[[法方程]]的系数矩阵[[非奇异]]，于是法方程存在**唯一的解** $a_k=a_k^*,k=0,1,\cdotp\cdotp\cdotp,n$, 从而得到函数 $f(x)$ 的 *最小二乘解* 为
  $$
  \begin{aligned}S^*\left(x\right)=a_0^*\varphi_0(x)+a_1^*\varphi_1\left(x\right)+\cdots+a_n^*\varphi_n(x).\end{aligned}
  $$
  可以证明这样得到的 $S^*(x)$ ,对任何形如 $(2)$ 式的 $S(x)$ , 都有
  $$
  \sum_{i=0}^m\omega(x_i)[S^*(x_i)-f(x_i)]^2\leqslant\sum_{i=0}^m\omega(x_i)[S(x_i)-f(x_i)]^2,
  $$
  故$S^*(x)$确是所求最小二乘解.
- 给定 $f(x)$ 的离散数据 $\{(x_i,y_i),i=0,1,\cdotp\cdotp,m\}$，要确定 $\varphi$ 是困难的，一般可取 $\varphi=$ $\operatorname{span}\{1,x,\cdotp\cdotp\cdotp,x^n\}$, 但这样做当 $n{\geqslant}3$ 时，将出现系数矩阵 $G$ 为病态的问题，通常对 $n= 1$ 的简单情形都可通过求 法方程 得到 $S^*(x)$ . 
  有时根据给定数据图形，其拟合函数 $y=S(x)$ 表面上不是 $(2)$ 式的形式，但通过变换仍可化为线性模型.
	- 例如，$S(x)= a\mathrm{e}^{bx}$ , 若两边取对数得
	  $$
	  \ln S(x)=\ln a+bx\:,
	  $$
	  它就是形如 $(2)$ 式的线性模型.
- ## [[用多项式作最小二乘拟合]]
- ## 总结
- ### 为什么使用最小二乘法
	- 最小二乘法提供了一种在给定数据中寻找最佳拟合曲线或面的有效方法，尤其是在处理线性模型时。下面详细讨论使用最小二乘法的几个主要理由：
	- ### 1. 数学优化角度
		- **解析解的可得性**：对于线性模型，最小二乘法通常可以导出解析解，这意味着可以直接通过数学公式计算出参数的最优值，不需要复杂的迭代过程。这样可以快速有效地找到最优解。
		- **凸优化问题**：最小二乘法所涉及的优化问题是凸优化问题，这保证了找到的解是全局最优解，而非局部最优。这一点对于保证模型的稳定性和可靠性至关重要。
	- ### 2. 统计估计角度
		- **高斯-马尔可夫定理**：在满足一定条件（例如，误差项独立同分布，且具有常数方差）下，线性最小二乘估计量是最佳线性无偏估计（BLUE: Best Linear Unbiased Estimator）。这意味着在所有线性无偏估计中，最小二乘估计具有最小的方差，提供了对未知参数的最佳估计。
		- **简便性和普遍性**：最小二乘法不需要对数据分布做出严格假设，如正态分布等，这使得它在实际应用中更为灵活和广泛。
	- ### 3. 实际应用角度
		- **广泛的适用性**：最小二乘法不仅适用于线性模型，还可以通过多项式或其他基函数拓展到非线性模型，使得它能够广泛应用于各种科学和工程问题中。
		- **易于理解和实现**：最小二乘法的原理直观易懂，且容易通过现有的数学软件和编程语言实现，这为研究人员和工程师提供了极大的便利。
		- **鲁棒性和效率**：尽管最小二乘法对异常值比较敏感，但其在大多数标准应用场景下表现出了良好的鲁棒性和高效性，尤其是在数据点数量众多时。