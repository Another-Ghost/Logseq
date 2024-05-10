alias:: 映射, 算子, maps

- 设$X$、$Y$是两个非空集合，如果存在一个[[对应法则]]$f$，使得对$X$中的每个元素$x$，按法则$f$，在$Y$中有*唯一*的元素$y$与之对应，那么称$f$为从$X$到$Y$的一个[[mapping]]（mapping of $X$ **into** $Y$），记作：
- $$f:X\to Y$$
- >映射$f$记作：$f:X\to Y$，法则$f$记作：$f$
- 其中$y$称为$x$在映射$f$下的[[image]]，并记作$f(x)$，即$y=f(x)$。
- $x$称为$y$在映射$f$下的一个[[inverse image]]。
- $X$称为映射$f$的[[domain of definition]]，记作$$D_f=X$$。
- $Y$称为映射$f$的[[陪域]]，记作$C_f=Y$。
- $X$中所有元素的[[image]]所组成的集合称为映射$f$的[[range]]，记作$R_f$或$f(X)$，即$R_f=f(X)=\{f(x)|x\in X\}$。
- 对每个$y\in R_f$，$y$的[[inverse image]]**不一定是唯一的**。
- 映射$f$的[[range]]$R_f$是[[陪域]]$Y$的一个**子集**，即$R_f\subseteq Y$。
-
- 若$f:X\rightarrow Y$，$g:X\rightarrow Y$，且$f(a)=g(a)$，$\forall a\in X$，则称$f$与$g$**相等**，记作$f=g$。
-
- # 映射的乘法，可逆映射
	- ## 定义1
		- 设映射$f:A\rightarrow B$，$g:B\rightarrow C$，令$(gf)(a)=g(f(a)), \forall a\in A$，则称$gf$是$g$与$f$的**乘积**（或**合成**）。
	- 映射的乘法满足[[结合律]]。
	- 映射的乘法[[不满足交换律]]。
	- ## 定义2
		- 对于映射：
		  $$f:A\longrightarrow A, $$
		  $$a\longmapsto a，\forall a\in A$$
		  则$f$是$A$上的[[恒等变换]]，记作$1_A$。
	- ## 命题1
		- 设$f:A\rightarrow B$，则
			- $$f1_A=f,\quad 1_Bf=f$$
			- $$(f1_A)(a)=f(a), \quad (1_Bf)(a)=f(a),\quad\forall a\in A$$
	- ## 定义3
		- 设映射$f: A\longrightarrow B$，如果存在$g: B\longrightarrow A$，使得$gf=1_A$且$fg=1_B$，那么称$f$[[可逆映射]]，把$g$称为$f$的[[逆映射]]。
		- 若$f$可逆，则$f$的逆映射唯一。
		- 把$f$的逆映射记作$f^{-1}$。此时有$f^{-1}f=1_A$且$ff^{-1}=1_B$。因此$f^{-1}$也是可逆映射，且$(f^{-1})^-1=f$。
		- ## 定理1
		- $f:A\rightarrow B$是可逆映射$\Longleftrightarrow f$是[[bijection]]。