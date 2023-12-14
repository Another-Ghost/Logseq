alias:: 矩阵的 LU 分解, LU 分解定理

- # Theorem
	- 设 $\boldsymbol A$ 为 $n$ 阶[[矩阵]]，如果 $\boldsymbol A$ 的[[顺序主子式]] $D_i\neq0$ ($i=$ $1,2,...,n-1)$,则 $\boldsymbol A$ 可分解为一个[单位下三角矩阵]([[单位下三角矩阵]])$\bolL$ 和一个[[上三角矩阵]]$U$ 的[[乘积]]，且这种分解是[[唯一]]]的:
	  logseq.order-list-type:: number
		- $$\left[\begin{array}{cccc}
		  1 \\
		  l_{21} & 1 \\
		  \vdots & \vdots & \ddots \\
		  l_{n1} & l_{n2} & \cdots, & 1
		  \end{array}\right]$$
		- $L$ 为一般[[下三角阵]]而 $U$ 为[[单位上三角阵]]的分解称为[[Crout 分解]]。
			- 实际上只要考虑 $A^\mathrm{T}$ 的[[LU 分解]]，即 $A^T=LU$, 则 $A=U^{T} L^{T}$ 即是 $A$ 的[[Crout 分解]]。
-