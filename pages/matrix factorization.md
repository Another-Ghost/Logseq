alias:: 三角分解法, 矩阵的三角分解

- # [[Gauss 消去法的矩阵形式]]
	- #+BEGIN_PINNED
	  ![image.png](../assets/image_1701887543381_0.png){:height 338, :width 658}
	  ![image.png](../assets/image_1701887591367_0.png)
	  ![image.png](../assets/image_1701887712113_0.png) 
	  #+END_PINNED
- # Theorm
	- ## [[矩阵的 LU 分解]]
	  logseq.order-list-type:: number
	  设 $\boldsymbol A$ 为 $n$ 阶[[矩阵]]，如果 $\boldsymbol A$ 的[[顺序主子式]] $D_i\neq0$ ($i=$ $1,2,...,n-1)$,则 $\boldsymbol A$ 可分解为一个[单位下三角矩阵]([[单位下三角矩阵]])$L$ 和一个[[上三角矩阵]]$U$ 的[[乘积]]，且这种分解是[[唯一]]]的.
		- $L$ 为一般[[下三角阵]]而 $U$ 为[[单位上三角阵]]的分解称为[[Crout 分解]]。
			- 实际上只要考虑 $A^\mathrm{T}$ 的[[LU 分解]]，即 $A^T=LU$, 则 $A=U^{T} L^{T}$ 即是 $A$ 的[[Crout 分解]]。
- # [[直接三角分解法]]