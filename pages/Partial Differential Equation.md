alias:: PDE, 偏微分方程

- ## 偏微分方程定义
	- 一个偏微分方程是关于未知函数及其[[偏导数]]的方程。这个未知函数是两个或多个自变量的函数。偏微分方程形式上可以表示为：
	  $$ F(x_1, x_2, \ldots, x_n, u, \frac{\partial u}{\partial x_1}, \frac{\partial u}{\partial x_2}, \ldots, \frac{\partial^2 u}{\partial x_1^2}, \frac{\partial^2 u}{\partial x_1 \partial x_2}, \ldots) = 0 $$
	  其中，\( x_1, x_2, \ldots, x_n \) 是自变量，\( u = u(x_1, x_2, \ldots, x_n) \) 是未知函数，\( \frac{\partial u}{\partial x_i} \) 和 \( \frac{\partial^2 u}{\partial x_i \partial x_j} \) 分别是 \( u \) 的一阶和二阶偏导数，\( F \) 是给定的函数。
- ### 偏微分方程的分类
	- 1. **根据阶数（Order）**：偏微分方程可以根据涉及的最高阶偏导数的阶数来分类。例如，二阶偏微分方程涉及未知函数的二阶偏导数。
	- 2. **线性与非线性（Linear and Non-linear）**：
		- **线性偏微分方程**：如果 \( F \) 是关于 \( u \) 及其偏导数的线性函数，则方程是线性的。
		- **非线性偏微分方程**：如果 \( F \) 对 \( u \) 或其偏导数是非线性的，则方程是非线性的。
	- 3. **齐次与非齐次（Homogeneous and Non-homogeneous）**：
		- **齐次偏微分方程**：如果 \( F = 0 \) 是齐次函数，则方程是齐次的。
		- **非齐次偏微分方程**：如果 \( F \) 不是齐次函数，则方程是非齐次的。
-