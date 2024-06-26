alias:: 回归系数

- 在统计学中，[[回归系数]]是[[回归模型]]中用于预测目标变量（或因变量）的自变量（或解释变量）的系数。这些系数表示自变量对目标变量的平均影响强度。
  举个例子，考虑一个简单的线性回归模型：
  $$ y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n + \epsilon $$
  
  在这个模型中：
	- \( y \) 是目标变量。
	- \( x_1, x_2, \ldots, x_n \) 是自变量。
	- \( \beta_0 \) 是截距项（intercept），它是当所有自变量为零时目标变量的[[期望值]]。
	- \( \beta_1, \beta_2, \ldots, \beta_n \) 是回归系数，表示每个自变量对目标变量的影响。
	- \( \epsilon \) 是误差项，代表了模型中未能解释的变异性。
- 回归系数可以通过[[最小二乘法]]等统计方法估计。
  在最小二乘法中，回归系数的估计旨在最小化实际观测值和模型预测值之差的平方和。
  回归系数的估计值告诉我们：
	- **系数的符号**（正或负）表明自变量与目标变量之间的关系是正向的还是负向的。
	- **系数的大小**表明自变量变化一个单位时目标变量平均变化的数量。
	- 如果回归系数为零，则表明自变量和目标变量之间没有线性关系。