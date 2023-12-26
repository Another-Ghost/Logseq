alias:: 松弛法

- [[松弛法]]可以看作是[[高斯-赛德尔方法]]的一个推广或改进。
- ## 松弛法
  松弛法引入了一个[[松弛因子]] \( \omega \)（\( 0 < \omega < 2 \)）到高斯-赛德尔方法
  {{embed ((658710b0-a3e4-40aa-ad86-1136d2d94651))}}
  中，其迭代公式为：
  \[ x_i^{(k+1)} = (1 - \omega)x_i^{(k)} + \frac{\omega}{a_{ii}} \left( b_i - \sum_{j=1}^{i-1} a_{ij}x_j^{(k+1)} - \sum_{j=i+1}^{n} a_{ij}x_j^{(k)} \right) \]
	- ### 松弛因子 \( \omega \)
		- \( \omega < 1 \)：称为[[低松弛法]]，有助于提高方法的[[稳定性]]。
		- \( \omega = 1 \)：此时，SOR方法就是[[高斯-赛德尔方法]]。
		- \( \omega > 1 \)：称为[[超松弛]]，目的是加速收敛。
		  id:: 65870db5-e8af-4096-b018-51fee7aeac60
- ## 矩阵形式
	- 对于线性方程组 \( \boldsymbol{A}\boldsymbol{x} = \boldsymbol{b} \)，将 \( \boldsymbol{A} \) 分解为对角部分 \( \boldsymbol{D} \)，严格下三角部分 \( \boldsymbol{L} \) 和严格上三角部分 \( \boldsymbol{U} \)，即 \( \boldsymbol{A} = \boldsymbol{D} - \boldsymbol{L} - \boldsymbol{U} \)。
	  SOR的逐元素更新公式可以重写为矩阵形式：
	  \[ \boldsymbol{x}^{(k+1)} = \boldsymbol{x}^{(k)} + \omega (\boldsymbol{D} - \omega \boldsymbol{L})^{-1} \left( \boldsymbol{b} - (\boldsymbol{D} - \boldsymbol{L} - \boldsymbol{U})\boldsymbol{x}^{(k)} + \boldsymbol{L}(\boldsymbol{x}^{(k+1)} - \boldsymbol{x}^{(k)}) \right) \]
	  重新排列后得到：
	  \[ (\boldsymbol{D} - \omega \boldsymbol{L})\boldsymbol{x}^{(k+1)} = (1 - \omega)\boldsymbol{D}\boldsymbol{x}^{(k)} + \omega \boldsymbol{U}\boldsymbol{x}^{(k)} + \omega \boldsymbol{b} \]
	  因此，SOR方法的矩阵形式为：
	  \begin{aligned} \boldsymbol{x}^{(k+1)} &= (\boldsymbol{D} - \omega \boldsymbol{L})^{-1} \left( (1-\omega)\boldsymbol{D} + \omega \boldsymbol{U} \right) \boldsymbol{x}^{(k)} + \omega (\boldsymbol{D} - \omega \boldsymbol{L})^{-1} \boldsymbol{b} \\
	  &=\boldsymbol H_\omega \boldsymbol x^{(k)}+\boldsymbol f\end{aligned}
		- 其中 $\boldsymbol H_\omega$ 称为[[松弛迭代阵]]。
- ## Theorem
	- 设 $\boldsymbol A$ 可逆，且 $a_{ii}\neq0$ ，松弛法从任意$\boldsymbol{x}^{(0)}$出发对某个 $\omega$ 收敛 $\Leftrightarrow\rho(\boldsymbol H_{\omega})<1$。
	  logseq.order-list-type:: number
	- ### Kahan 必要条件
	  logseq.order-list-type:: number
	  设 $\boldsymbol A$ 可逆，且$a_{ii}\neq0$, 松弛法从任意 ${x}^{(0)}$ 出发收敛 $\Rightarrow0<\omega<2$ 。
	- ### Ostrowski-Reich 充分条件 
	  logseq.order-list-type:: number
	  若 $A$ [[对称正定]]，且有 $0<\omega<2$ ，则松弛法从任意$\boldsymbol{x}^{(0)}$ 出发收敛。
	- 若$\boldsymbol A$ 为[[对称正定三对角阵]]，则 $\rho(\boldsymbol B_{G-S})=[\rho(\boldsymbol B_J)]^2<1$ 且SOR的[[最佳松弛因子]]为 $\omega=\frac{2}{1+\sqrt{1-[\rho(\boldsymbol B_j)]^2}}$  ，此时 $\rho(\boldsymbol H_{\omega})=\omega-1$ 。
	  logseq.order-list-type:: number