alias:: 向量函数的微分, 向量函数的导数

- # Definition
  id:: 64fa6aa9-55a2-4c1c-a5c7-6d994f8c96b9
	- Let $\mathbf{f}:(a, b) \rightarrow R^{k}$ and $x \in(a, b)$, we say $\mathbf{f}$ is [[differentiable]] at $x$, provided that $\mathbf{f}^{\prime}(x)=\lim _{t \rightarrow x} \frac{\mathbf{f}(t)-\mathbf{f}(x)}{t-x}$ **exists**.
	  logseq.order-list-type:: number
		- >Let $f:(a, b) \rightarrow R$ and $c \in(a, b)$.
		  If $f$ is differentiable at $c$ , then  $\exists \mathrm{g} \cdot(a, b) \rightarrow R^{k}$ which is [[contimnous]] at  $c$  such that
		  $$\mathbf{f}(x)=\mathbf{f}(c)+\mathbf{f}^{\prime}(c)(x-c)+(x-c) \mathbf{h}(x)$$
		  for all $x \in(a, b)$, with $\mathbf{h}(c)=0$.
	- 设 $D\subset\mathbb{R}^{n}$ 为[[开集]], $\bold{x}_0\in D,f:D{\to}\mathbb{R}^m$. 
	  logseq.order-list-type:: number
		- 如果存在某个[[线性变换]] $\cal A$（只依赖于$\bold{x}_0$）, 使得 $\bold{x}\in U(\bold{x}_0)\subset D$（$\bold{x}$ 足够靠近 $\bold{x}_0$）时, 有
		  logseq.order-list-type:: number
		  $$
		  f\left(\bold{x}\right)-f\left(\bold{x}_{0}\right)=\cal{A}\left(\bold{x-x}_{0}\right)+o\left(\parallel \bold{x-x}_{0}\parallel\right) \tag{1}
		  $$
		  ([[向量范数]])或
		  $$
		  \lim_{\bold{x\to x}_0}\frac{f\left(\bold{x}\right)-f\left(\bold{x}_0\right)-\mathcal A\left(\bold{x}-\bold{x}_0\right)}{\left\Vert \bold{x-x}_0\right\Vert}=\bold{0}
		  $$
		  则称[[向量函数]] $f$ 在点 $\bold{x}_0$ [[可微]](或[[可导]]).
		- 若与上述[[线性变换]] $\cal A$ 相联系的[[矩阵]]为 $\boldsymbol{A}_{_{m\times n}}$ , 则称 
		  logseq.order-list-type:: number
		  $$\mathcal{A}\left({\boldsymbol{x}}-{\bold{x}}_{0}\right)=\boldsymbol{A}\left({\bold{x}}-{\bold{x}}_{0}\right)$$ 
		  为 $f$ 在点 $\bold{x}_0$ 的[[微分]], 并称$\boldsymbol{A}$ 为 $f$ 在点 $\bold{x}_0$ 的[[导数]], 记作 $D f(\bold{x}_0)$ 或 $f^{\prime}\left(\bold{x}_{0}\right)$. 
		  因而
		  \begin{aligned}
		  \mathcal{A}\left(\bold{x}-\bold{x}_{0}\right) &=\boldsymbol{A}\left(\bold{x}-\bold{x}_{0}\right)=Df\left(\bold{x}_{0}\right)\left(\bold{x}-\bold{x}_{0}\right) \\
		  &=f^{\prime}(\bold{x}_{0})(\bold{x}-\bold{x}_{0})
		  \end{aligned}
		  同样是 $f\left(\bold{x}\right)-f\left(\bold{x}_{0}\right)$ 的[[最佳线性逼近]].
		- 如果 $f$ 在 $D$ 中**任何点**处[[可微]]，则称 $f$ 为 $D$ 上的[[可微函数]]. 
		  logseq.order-list-type:: number
		- 设
		  logseq.order-list-type:: number
		  $$
		  f=\begin{pmatrix}f_1\\\vdots\\f_m\end{pmatrix},\quad\boldsymbol{A}=\begin{pmatrix}a_{11}&\cdots&a_{1n}\\\vdots&&\vdots\\a_{m1}&\cdots&a_{mn}\end{pmatrix}=\begin{pmatrix}\boldsymbol{A}_1^\mathrm{T}\\\vdots\\\boldsymbol{A}_m^\mathrm{T}\end{pmatrix}
		  $$
		  其中 $\boldsymbol{A}_{i}=(a_{i1},\cdots,a_{in})^{T},i=1,2,\cdots,m$ 此时, [[可微]]条件 $(1)$ **等价于**
		  $$f_{i}(\bold{x})-f_{i}(\bold{x}_{0})=\boldsymbol{A}_{i}^{T}(\bold{x}-\bold{x}_{0})+o(\|\bold{x}-\bold{x}_{0}\|), i=1 ,2,\cdots,m$$
		  则 $f$ 的所有[[坐标函数]] $f_{i}(i=1,2,\cdots,m)$ 在 $\bold{x}_{0}$ [[可微]]. 由[实值函数可微性]([[differentiation of real function]])的结论知道
		  $$
		  a_{ij}=\frac{\partial f_{i}}{\partial x_{j}}\Bigg|_{\mathbf{x}=\mathbf{x}_{0}},\quad j=1,2,\cdots,n; \quad i=1,2\:,\cdots,m
		  $$
		  于是当 $f$ 在 $\bold{x}_0$ [[可微]]时 $f$ 在 $\bold{x}_{0}$ 的[[导数矩阵]]为 [[雅可比矩阵]] $\boldsymbol{J}_f(\bold{x}_0)$:
		  $$
		  \boldsymbol{A}
		  =\begin{pmatrix}\frac{\partial f}{\partial x_1}&\cdots \frac{\partial f}{\partial x_n}\end{pmatrix}\bigg|_{\left\{x_1,\cdots,x_n\right\}=\bold{x}_0}
		  =\begin{pmatrix}\frac{\partial f_1}{\partial x_1}&\cdots&\frac{\partial f_1}{\partial x_n}\\\vdots&&\vdots\\\frac{\partial f_m}{\partial x_1}&\cdots&\frac{\partial f_m}{\partial x_n}\end{pmatrix}\bigg|_{\left\{x_1,\cdots,x_n\right\}=\bold{x}_0}=f'(\bold{x}_0)=D f(\bold{x}_0)
		  $$
- # Theorem
	- Let $\mathbf{f}=\left(f_{1}, \ldots, f_{k}\right)$, then $\mathbf{f}$ then $\mathbf{f}$ is [[differentiable at a point]]  $x$  **if and only if** each of the component functions  $f_{1}, \ldots, f_{k}$ is **differentiable** at $x$, and
	  logseq.order-list-type:: number
	  $$\mathbf{f}^{\prime}=\left(f_{1}^{\prime}, \ldots, f_{k}^{\prime}\right)$$
	- Suppose $\mathbf{f}$ and $\mathbf{g}$ are defined on $[a, b]$ and are [[differentiable]] at a point $x\in [a, b]$. Then $\mathbf{f}+ \mathbf{g}$, $\mathbf{f}\cdot\mathbf{g}$([[inner product]]), and are **differentiable** at $x$, and
	  logseq.order-list-type:: number
		- $(\mathbf{f} + \mathbf{g})'(x) = \mathbf{f}'(x) + \mathbf{g}'(x)$;
		  logseq.order-list-type:: number
		- $(\mathbf{f}\cdot\mathbf{g})'(x) = \mathbf{f}'(x)\cdot\mathbf{g}(x) + \mathbf{f}(x)\cdot\mathbf{g}'(x)$;
		  logseq.order-list-type:: number
	- Suppose $\mathbf{f}$ is a [[continuous]] mapping of $[a, b]$ into $R^k$ and $\mathbf{f}$ is [[differentiable]] in $(a, b)$. Then there exists $x\in(a, b)$ such that 
	  logseq.order-list-type:: number
	  $$|f(b) - f(a)|\le (b - a)|f'(x)|$$
		- >The [[mean value theorem]] fails for [[vector-valued function]].
	- > 由于[[向量函数]]的[[可微性]]**等价于**它的所有[[坐标函数]]的[[可微性]], 因此,*实值函数可微* 的**必要条件**与**充分条件**同样适用于 *向量函数* .
-