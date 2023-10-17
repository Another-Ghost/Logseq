alias:: 柯西-黎曼方程, C-R方程

-
- # Theorem Description 1
	- Suppose $f$ is a [[complex function]] in $0$ that has a [[differential]] at 
	  **every** *point* of $\Omega$. Then $f\in H(\Omega)$([[holomorphic function]]) **if and only if** the [[Cauchy-Riemann equation]]
	  $$(\bar{\partial}f)(z)=0 \tag{1}$$
	  ([[differential operator]])holds for every $z ∈\Omega$.
		- >[Proof](https://www.bilibili.com/video/BV1w54y1m7Wb?t=173.7&p=32)
	- In that case we have
	  $$
	  f^{\prime}(z)=(\partial f)(z)\quad\quad(z\in\Omega)
	  $$
	- If $f = u + iv$, $u$ and $v$ are [[real]], $(1)$ splits into the pair of equations
	  $$
	  u_{x}=v_{y},\quad u_{y}=-v_{x}
	  $$
	  ([[partial differentiation]])
- # Theorem Description 2
	- 函数 $f\left(z\right)=u\left(x,y\right)+\mathrm{i}v\left(x,y\right)$ 在 $z=x+\mathrm{i}y$ 处[可导]([[complex differentiable]])的**充要条件**是
	  collapsed:: true
	  $u\left(x,y\right),v\left(x,y\right)$在点 $(x,y)$ 处[[可微]]，而且满足[[柯西-黎曼方程]]:
	  $$
	  \frac{\partial u}{\partial x}=\frac{\partial v}{\partial y},\quad\frac{\partial u}{\partial y}=-\:\frac{\partial v}{\partial x}
	  $$
		- 当定理的条件满足时,可按下列公式之一计算$f^{\prime}\left(z\right)$:
		  \begin{aligned}
		  f^{\prime}\left(z\right)& =\frac{\partial u}{\partial x}+\text{i}\frac{\partial v}{\partial x}=\frac{\partial v}{\partial y}+\text{i}\frac{\partial v}{\partial x}  \\
		  &=\frac{\partial u}{\partial x}-\mathrm{i}\frac{\partial u}{\partial y}=\frac{\partial v}{\partial y}-\mathrm{i}\frac{\partial u}{\partial y}
		  \end{aligned}
		- >$u,v$*偏导数**连续* $\Longrightarrow$ *可微*