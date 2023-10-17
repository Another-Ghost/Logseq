alias:: differential opetators, 微分算子

- # Defintion
	- Suppose $f$ is a [[complex function]] defined in a [[plane open set]] $\Omega$. Regard $f$ as a transformation which maps $\Omega$ into $R^2$, and assume that $f$ has a [[differential]] at some point $z_0\in \Omega$.
	  For simplicity, suppose $z_0 = f(z_0) = 0$. Our [[differentiability]] assumption is then equivalent to the existence of two [[complex numbers]] $\alpha$ and $\beta$ (the [[partial derivatives]] of $f$ with respect to $x$ and $y$ at $z_0=0$) such that
	  $$f(z)=\alpha x+\beta y+\eta(z)z\quad (z=x+iy) \tag{1}$$
	  where $\eta(z)→0$ as $z→0$.
	  Since $2x=z+\bar{z}$ and $2iy = z -\bar{z}$, $(1)$ can be rewritten in the form
	  $$f(z)=\frac{\alpha-i\beta}{2}z+\frac{\alpha+i\beta}{2}\bar{z}+\eta(z)z \tag{2}$$
	  This suggests the introduction of the [[differential operators]]
	  \begin{aligned} \partial=\frac12\left(\frac\partial{\partial x}-\mathrm{i~}\frac\partial{\partial y}\right) \\ \quad\bar{\partial}=\frac12\left(\frac\partial{\partial x}+\mathrm{i~}\frac\partial{\partial y}\right)\end{aligned}
	- Now $(2)$ becomes
	  $$
	  \frac{f(z)}z=(\partial f)(0)+(\bar{\partial}f)(0)\cdot\frac{\bar{z}}z+\eta(z)\quad\quad(z\neq0)
	  $$
	  For [[real]] $z$, $\frac{\bar{z}}{z} = 1$; for [[pure imaginary]] $z$, $\frac{\bar{z}}{z} = -1$. Hence $\frac{f(z)}{z}$ has a [[limit]] 
	  at $0$ **if and only if** $(\bar{\partial}f)(0) = 0$.
-