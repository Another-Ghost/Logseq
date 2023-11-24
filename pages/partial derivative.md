alias:: 偏导数, partial derivatives, partial differentiation, partial differentiations

- [[函数]]$\boldsymbol f$ 把 [[开集]]$E{\subset}\mathbb{R}^n$ 映入 $\mathbb{R}^m$ . 设 $\{\boldsymbol e_1,\cdots, \boldsymbol e_n\}$ 及 $\{\boldsymbol u_1,\cdots, \boldsymbol u_m\}$分别是 $R^n$ 及 $R^m$ 的[[标准基]]。$\boldsymbol f$ 的[[分量]]是由
  id:: 655f636b-c852-4805-8828-90be940f31ff
  $$
  \boldsymbol f(\boldsymbol x)=\sum_{i=1}^{m}f_{i}(\boldsymbol x)\boldsymbol u,\quad(\boldsymbol x\in E), \tag{1}
  $$
  确定的[[实函数]] $f_1,\cdots,f_{m}$； 
  上式还可以等价地写成
  $$
  f_{i}(\boldsymbol x)=\boldsymbol{f}(\boldsymbol x)\cdot\boldsymbol{u}_{i},\quad 1\le i\le m.$$
- 对于 $\boldsymbol x\in E$, $1\le i\le m$, $1\le j\le n$ 定义
  id:: 655f66cc-bfc6-4ef8-a450-eb25f2146c8d
  $$
  (D_j f_i)(\boldsymbol x)=\lim_{t\to0}\frac{f_{i}(\boldsymbol x+t\boldsymbol e_{j})-f_{i}(\boldsymbol x)}t,
  $$
  这里假定此[[极限]]存在。把 $f_i(x)$ 写成$f_i(x_1,\cdots,x_i)$，就知道 $D_if_i$ 是 $f_i$ 对于 $x_j$ 的[[导数]](其他变量保持不变)。所以，经常用记号
  $$\frac{\partial f_i}{\partial x_j}$$
  代替$D_j,f_i$，而$D_if_i$被叫做[[偏导数]]。
- # Theorem
	- 设 $\boldsymbol f$ 把 开集$E\subset \mathbb R^n$ 映入$\mathbb R^m$ 内，$\boldsymbol f$ 在点 $\boldsymbol x\in E$[[可微]]。
	  logseq.order-list-type:: number
	  那么，[[偏导数]] $D_jf_i(\boldsymbol x)$ 存在，且
	  $$
	  \boldsymbol{f}^{\prime}(\boldsymbol x)\boldsymbol{e}_{j}=\sum_{i=1}^{n}(D_{j}f_{i})(\boldsymbol x)\boldsymbol{u}_{i}, \quad 1\le j\le n .
	  $$
	  $\{\boldsymbol e_1,\cdots, \boldsymbol e_n\}$ 及 $\{\boldsymbol u_1,\cdots, \boldsymbol u_m\}$ 分别是 $\mathbb R^n$ 及 $\mathbb R^m$ 的[[标准基]].
		- ## Corollary
			- 令 $[\boldsymbol f^{\prime}(\boldsymbol x)]$ 是关于上述标准基的$\boldsymbol f^{\prime}(\boldsymbol x)$的表现矩阵。那么$\boldsymbol f^{\prime}(\boldsymbol x)\boldsymbol e$ 是$[\boldsymbol f^{\prime}(\boldsymbol x)]$ 的第 $j$ 个 *列向量* ，$(1)$式
			  logseq.order-list-type:: number
			  id:: 6560e6d6-984e-4a83-9958-98553ccfbcf7
			  $$
			  \boldsymbol f(\boldsymbol x)=\sum_{i=1}^{m}f_{i}(\boldsymbol x)\boldsymbol u,\quad(\boldsymbol x\in E)
			  $$
			  说明 数$(D_jf_i)(\boldsymbol x)$ 占有$[\boldsymbol f^{\prime}(\boldsymbol x)]$的第 $i$ 行第 $j$ 列的位置。即是
			  $$
			  [\boldsymbol f^{\prime}(\boldsymbol x)]=\begin{bmatrix}(D_1f_1)(\boldsymbol x)&\cdots&(D_nf_1)(\boldsymbol x)\\\cdots&\cdots&\cdots\\(D_1f_m)(\boldsymbol x)&\cdots&(D_nf_m)(\boldsymbol x)\end{bmatrix}.
			  $$
			  如果 $\boldsymbol h=\sum\boldsymbol h_j\boldsymbol e_j$ 是$R^n$ 中的任何向量，那么，由 $(1)$ 式说明
			  $$
			  \boldsymbol f^{\prime}(\boldsymbol x)\boldsymbol h=\sum_{i=1}^{m}\left\{\sum_{j=1}^{n}(D_{j}f_{i})(\boldsymbol x)\boldsymbol h_{j}\right\}\boldsymbol u_{i}.
			  $$
			- logseq.order-list-type:: number
-