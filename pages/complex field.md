alias:: 复数域, complex numbers, complex, 复数

- # Definition
	- A [[complex number]] is an [[ordered pair]] $(a, b)$ of [[real numbers]].
	  logseq.order-list-type:: number
	- Let $z_1 = (x_1, y_1)$, $z_2 = (x_2, y_2)$ be two [[complex numbers]]. We write $z_1 = z_2$ **if and only if** $x_1= x_2$ and $y_1 = y_2$.
	  logseq.order-list-type:: number
	- We define
	  logseq.order-list-type:: number
	  \begin{aligned}
	  z_1 + z_2 & = (x_1 + x_2, y_1 + y_2) \\ 
	  z_1z_2 & = (x_1x_2 - y_1y_2, x_1y_2+ x_2y_1)
	  \end{aligned}
	- These definitions of [[addition]] and [[multiplication]] turn the set of all complex numbers into a [[field]], with $(0, 0)$ and $(1, 0)$ in the role of $0$ and $1$.
	  logseq.order-list-type:: number
	- $i = (0, 1)$.
	  logseq.order-list-type:: number
	- If $x, y$ are real and $z =x+ yi$, then the complex number $\overline{z} = x - yi$ is called the [[conjugate]] of $z$. The numbers $x$ and $y$ are the [[real part]] and the [[imaginary part]] of $z$, respectively.
	  logseq.order-list-type:: number
	  We shall occasionally write
	  $$x= \mathrm{Re}(z), \quad y = \mathrm{Im}(z)$$
	- If $z$ is a complex number, its [[absolute value]] $\left |z \right |$ is the non-negative [[square root]] of $z\overline{z}$; that is, 
	  logseq.order-list-type:: number
	  $$\left |z \right | = (z\overline{z})^{1/2}$$
	  >$$z\cdot\overline{z}=x^2+y^2, \ x=\frac{z+\overline{z}}{2}, \ y=\frac{z-\overline{z}}{2i}$$
- # Theorem
	- For any real numbers $a$ and $b$ we have
	  logseq.order-list-type:: number
	  $$(x, 0) + (y, 0) = (x + y, 0),\quad (x, 0)(y, 0) = (xy, 0)$$
		- This theorem shows that the complex numbers of the form $(x, 0)$ have the same arithmetic properties as the corresponding real numbers $x$. We can therefore identify $(x, 0)$ with $x$. This identification gives us the [[real field]] as a [[subfield]] of the [[complex field]].
	- $i^2 = -1$.
	  logseq.order-list-type:: number
	- If $x$ and $y$ are real, then $(x, y) =x+ yi$.
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number
	  $$\frac{z_1}{z_2}=\frac{(x_1x_2+y_1y_2)-i(x_1y_2+y_1x_2)}{{x_2}^2+{y_2}^2}, \quad z_2\ne 0$$
	  >$\frac{z_1}{z_2}=\frac{(x_1+iy_1)(x_2-iy_2)}{(x_2+iy_2)(x_2-iy_2)}$
	- If $z$ and $w$ are complex, then
	  logseq.order-list-type:: number
		- logseq.order-list-type:: number
		  $$\overline{z + w} = \overline{z} + \overline{w}$$
		- logseq.order-list-type:: number
		  $$\overline{zw}=\overline{z} \cdot \overline{w}$$
		- logseq.order-list-type:: number
		  $$\overline{\left(\frac{z}{w}\right)}=\frac{\overline{z}}{\overline{w}}$$
		- logseq.order-list-type:: number
		  $$z+\overline{z}=2 \operatorname{Re}(z), \ z-\overline{z}=2i \operatorname{Im}(z)$$
		- $z\overline{z}$  is real and [[positive]] (*except* when $z=0$).
		  logseq.order-list-type:: number
		- To prove e., write $z = x + yi$, and note that $z\overline{z} = x^2 + y^2$.
	- Let $z$ and $w$ be complex numbers. Then
	  logseq.order-list-type:: number
		- (a) $|z|>0$ unless $z=0,\ |0|=0$,
		- (b) $|\overline{z}|=|z|$,
		- (c) $|z w|=|z||w|$,
		- (d) $|\operatorname{Re} z| \leq|z|$,
		- (e) $|z+w| \leq|z|+|w|$.
		- If $a_1, \cdots, a_n$ and $b_1,\cdots, b_n$, bn are complex numbers, then
		  $$\left|\sum_{j=1}^{n} a_{j} \overline{b}_{j}\right|^{2} \leq \sum_{j=1}^{n}\left|a_{j}\right|^{2} \sum_{j=1}^{n}\left|b_{j}\right|^{2}$$