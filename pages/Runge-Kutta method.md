alias:: 龙格-库塔法, R-K 法

- #+BEGIN_TIP
  考察改进欧拉法, 可以将其改写为:
  $$\left\{\begin{array}{l}
  y_{n+1}=y_{n}+h\left[\frac{1}{2} K_{1}+\frac{1}{2} K_{2}\right] \\
  K_{1}=f\left(x_{n}, y_{n}\right) \\
  K_{2}=f\left(x_{n}+h, y_{n}+h K_{1}\right)
  \end{array}\right.$$
  显然,  $k_{1}$, $k_{2}$  是在点  $x_{n}, x_{n+1}$  处的斜率。以上公式用到的是两个点的斜率的加权平均, 它为构造算法提供了新的途径。Runge-Kutta方法就是这种思想的体现和发展。
  #+END_TIP
- ## $2$ 阶龙格 - 库塔格式
	- 将[[改进欧拉法]]推广为：
	  $$\left\{\begin{array}{lll}
	  y_{n+1}=y_{n}+h\left[\lambda_{1} K_{1}+\lambda_{2} K_{2}\right] & \lambda_{1}+\lambda_{2}=1 \\
	  K_{1}=f\left(x_{n} y_{n}\right) & & \\
	  K_{2}=f\left(x_{n}+p h, y_{n}+p h K_{1}\right) & & 0<p \leq 1
	  \end{array}\right.$$
	  首先希望能确定系数 $\lambda_{1}$ 、 $\lambda_{2}$ 、 $p$  ，使得到的算法格式有 2 阶精度，即在  $y_{n}=y\left(x_{n}\right)$  的前提假设下，使得
	  $$T_{n+1}=y\left(x_{n+1}\right)-y_{n+1}=O\left(h^{3}\right)$$
		- 将  $K_{2}$  在  $\left(x_{n}, y_{n}\right)$  点作[泰勒展开]([[二元函数泰勒展开]])
		  logseq.order-list-type:: number
		  \begin{aligned}
		  K_{2} & =f\left(x_{n}+p h, y_{n}+p h K_{1}\right) \\
		  & =f\left(x_{n}, y_{n}\right)+p h f_{x}\left(x_{n}, y_{n}\right)+p h K_{1} f_{y}\left(x_{n}, y_{n}\right)+O\left(h^{2}\right) \\
		  & =y^{\prime}\left(x_{n}\right)+p h y^{\prime \prime}\left(x_{n}\right)+O\left(h^{2}\right)
		  \end{aligned}
			- #+BEGIN_TIP
			  \begin{aligned}
			  y^{\prime \prime}(x) & =\frac{d}{d x} f(x, y) \\
			  & =f_{x}(x, y)+f_{y}(x, y) \frac{d y}{d x} \\
			  & =f_{x}(x, y)+f_{y}(x, y) f(x, y)
			  \end{aligned}
			  #+END_TIP
		- 将  $K_{2}$  代入第 1 式，得到
		  logseq.order-list-type:: number
		  \begin{aligned}
		  y_{n+1} & =y_{n}+h\left\{\lambda_{1} y^{\prime}\left(x_{n}\right)+\lambda_{2}\left[y^{\prime}\left(x_{n}\right)+p h y^{\prime \prime}\left(x_{n}\right)+O\left(h^{2}\right)\right]\right\} \\
		  & =y_{n}+\left(\lambda_{1}+\lambda_{2}\right) h y^{\prime}\left(x_{n}\right)+\lambda_{2} p h^{2} y^{\prime \prime}\left(x_{n}\right)+O\left(h^{3}\right)
		  \end{aligned}
		- 将  $y_{n+1}$  与  $y\left(x_{n+1}\right)$  在  $x_{n}$  点的[[泰勒展开]]作比较
		  logseq.order-list-type:: number
		  \begin{array}{l}
		  y_{n+1}=y_{n}+\left(\lambda_{1}+\lambda_{2}\right) h y^{\prime}\left(x_{n}\right)+\lambda_{2} p h^{2} y^{\prime \prime}\left(x_{n}\right)+O\left(h^{3}\right) \\
		  y\left(x_{n+1}\right)=y\left(x_{n}\right)+h y^{\prime}\left(x_{n}\right)+\frac{h^{2}}{2} y^{\prime \prime}\left(x_{n}\right)+O\left(h^{3}\right)
		  \end{array}
		  要求  $T_{n+1}=y\left(x_{n+1}\right)-y_{n+1}=O\left(h^{3}\right)$ , 则必须有:
		  \begin{array}{l}
		  \lambda_{1}+\lambda_{2}=1, \lambda_{2} p=\frac{1}{2} 
		  \end{array}
		  这里有 $3$ 个未知数, $2$ 个方程，所以存在无穷多个解。
	- 所有满足上式的格式统称为 [[二阶龙格 - 库塔格式]]。注意到,
		- $p=1, \lambda_{1}=\lambda_{2}=\frac{1}{2}$  就是[[改进欧拉法]]。
		  logseq.order-list-type:: number
		- $p=1 / 2, \lambda_{1}=0, \lambda_{2}=1$  就是[[中点公式]]。
		  logseq.order-list-type:: number
		- $p=2 / 3, \lambda_{1}=1 / 4, \lambda_{2}=3 / 4$  就是[[休恩公式]]。
		  logseq.order-list-type:: number
- ## 显式龙格-库塔法的一般形式
	- $$y_{n+1}=y_{n}+h \sum_{i=1}^{L} \lambda_{i} k_{i} \tag{1}$$
	- \begin{array}{l}
	  k_{1}=f\left(x_{n}, y_{n}\right), \\
	  k_{2}=f\left(x_{n}+c_{2} h, y_{n}+c_{2} h k_{1}\right), \\
	  k_{3}=f\left(x_{n}+c_{3} h, y_{n}+c_{3} h\left(a_{31} k_{1}+a_{32} k_{2}\right)\right), \\
	  \cdots \cdots \\
	  k_{i}=f\left(x_{n}+c_{i} h, y_{n}+c_{i} h \sum_{j=1}^{i-1} a_{i j} k_{j}\right), \quad i=2,3, \cdots, L,
	  \end{array}
	  其中,  $\sum_{i=1}^{L} \lambda_{i}=1,0<c_{i} \leqslant 1, \sum_{j=1}^{i-1} a_{i j}=1$ .
	- 它的[[局部截断误差]]是
	  $$T_{n+1}=y\left(x_{n+1}\right)-y\left(x_{n}\right)-h \sum_{i=1}^{L} \lambda_{i} \bar{k}_{i},$$
	  其中,  $\bar{k}_{i}$  与  $k_{i}$  的区别在于: 
	  用微分方程精确解  $y\left(x_{n}\right)$  代替  $k_{i}$  中所含的  $y_{n}$  就得到  $\bar{k}_{i}$ . 参数  $\lambda_{i}$, $c_{i}$  和  $a_{i j}$  待定, 确定它们的原则和方法是: 
	  将式中的  $y\left(x_{n+1}\right)  在  x_{n}$  做[[泰勒展开]],  $\bar{k}_{i}$  在  $\left(x_{n}, y\left(x_{n}\right)\right)$  点做[[二元泰勒展开]], 将展开式按  $h$  的幂次整理后, 令  $T_{n+1}$  中  $h^{0}, h^{1}, h^{2}, \cdots$  项的系数为零, 使  $T_{n+1}$  首项中  $h$  的幂次尽量高.
	  比如, 使  $T_{n+1}=O\left(h^{p+1}\right)$ , 则称式 $(1)$ 为  $L$  级  $p$  阶[[龙格库塔法]]。
	- 最常用的[4 级 4 阶公式]([[四阶龙格-库塔法]])是如下的经典  R-K  方法
	  $$\begin{array}{l}
	  y_{n+1}=y_{n}+\frac{h}{6}\left(k_{1}+2 k_{2}+2 k_{3}+k_{4}\right), \\
	  k_{1}=f\left(x_{n}, y_{n}\right), \\
	  k_{2}=f\left(x_{n}+\frac{h}{2}, y_{n}+\frac{h}{2} k_{1}\right), \\
	  k_{3}=f\left(x_{n}+\frac{h}{2}, y_{n}+\frac{h}{2} k_{2}\right), \\
	  k_{4}=f\left(x_{n}+h, y_{n}+h k_{3}\right) .
	  \end{array}
	  $$
	- >前面已看到,  $L$  级 R-K 方法在  $L=1,2,3,4$  时, 可分别得到最高阶数  $1,2,3,4$  阶.但是, 通常  $L$  级  R-K  方法的最高阶不一定是  $L$  阶. 设  $P(L)$  是  $L$  级  R-K  方法可达到的最高阶数,可以证明如下.
	  $$P(5)=4, \quad P(6)=5, \quad P(7)=6, \quad P(8)=6, \quad P(9)=7 .$$
	- 由于龙格-库塔法的导出基于泰勒展开, 故精度主要受解函数的[[光滑性]]影响。对于光滑性不太好的解, 最好采用**低阶算法**而将步长  $h$  **取小**。
- ## 例子
	- 考虑常微分方程 \( \frac{dy}{dx} = f(x, y) \)，其中 \( f(x, y) = xy \)，并假设初始条件为 \( y(0) = 1 \)。我们希望使用四阶龙格-库塔法来计算 \( y(0.1) \) 的近似值。
	  
	  **步骤**：
		- 1. **选择步长**：假设我们选择步长 \( h = 0.1 \)。
		- 2. **计算** \( k_1, k_2, k_3, k_4 \)：
		- \( k_1 = f(x_n, y_n) = f(0, 1) = 0 \cdot 1 = 0 \)
		- \( k_2 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2} k_1) = f(0.05, 1 + 0.05 \cdot 0) = 0.05 \cdot 1 = 0.05 \)
		- \( k_3 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2} k_2) = f(0.05, 1 + 0.05 \cdot 0.05) = 0.05 \cdot 1.0025 \approx 0.050125 \)
		- \( k_4 = f(x_n + h, y_n + h k_3) = f(0.1, 1 + 0.1 \cdot 0.050125) \approx 0.100506 \)
		- 3. **更新 \( y_{n+1} \)**：
		  \[ y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4) \]
		  \[ y(0.1) \approx 1 + \frac{0.1}{6}(0 + 2 \cdot 0.05 + 2 \cdot 0.050125 + 0.100506) \]
		  \[ \approx 1 + \frac{0.1}{6}(0.250756) \]
		  \[ \approx 1.041793 \]
	- 因此，使用四阶龙格-库塔法，我们得到 \( y(0.1) \) 的近似值为 \( 1.041793 \)。
	  
	  **总结**：
	  
	  通过这个例子，我们可以看到四阶龙格-库塔法如何通过多次评估函数 \( f(x, y) \) 在不同点上的值来提高计算解的精度。这种方法广泛应用于求解微分方程，尤其在没有解析解的情况下非常有用。
- ## [[布彻表]]
	- 布彻表（Butcher Tableau）是一种用于描述和分析龙格-库塔方法的工具。在数值分析中，布彻表提供了一种结构化的方式来表示龙格-库塔法的系数。这些系数决定了在每一步中如何结合不同斜率的信息来估计下一个点的值。
	  
	  **布彻表的一般形式**：
	  
	  一个 \( s \) 阶龙格-库塔方法的布彻表可以表示为：
	  \begin{array}{c|cccc}
	  c_1 & a_{11} & a_{12} & \cdots & a_{1s} \\
	  c_2 & a_{21} & a_{22} & \cdots & a_{2s} \\
	  \vdots & \vdots & \vdots & \ddots & \vdots \\
	  c_s & a_{s1} & a_{s2} & \cdots & a_{ss} \\
	  \hline
	  & b_1 & b_2 & \cdots & b_s \\
	  \end{array}
	  这里：
		- \( c_i \) 表示用于计算斜率的点的权重。
		- \( a_{ij} \) 是系数矩阵，用于确定计算每个 \( k_i \) 时斜率的线性组合。
		- \( b_i \) 是权重，用于从各个斜率 \( k_i \) 中计算最终近似值。
	- **四阶龙格-库塔法的布彻表**：
	  作为一个特定的例子，标准的[[四阶龙格-库塔方法]]的布彻表如下：
	  \begin{array}{c|cccc}
	  0 & 0 & 0 & 0 & 0 \\
	  \frac{1}{2} & \frac{1}{2} & 0 & 0 & 0 \\
	  \frac{1}{2} & 0 & \frac{1}{2} & 0 & 0 \\
	  1 & 0 & 0 & 1 & 0 \\
	  \hline
	  & \frac{1}{6} & \frac{1}{3} & \frac{1}{3} & \frac{1}{6} \\
	  \end{array}