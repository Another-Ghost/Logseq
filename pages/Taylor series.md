alias:: 泰勒级数, Taylor expansion, 泰勒展开

- The [[Taylor series]] of a [[real]] or [[complex]] *function* $f$ that is [[infinitely]] [[differentiable]] **at** a [[real]] or [[complex]] number $a$ is the [[power series]]:
  $$\sum_{n=0}^{\infty}\frac{f^{(n)}(a)}{n!}(x-a)^n$$
- With $a=0$, The [[Maclaurin series]] takes the form:
  $$\sum_{n=0}^{\infty}\frac{f^{(n)}(0)}{n!}x^n$$
- # Examples
	- The Taylor series of any [[polynomial]] is the polynomial itself.
	  logseq.order-list-type:: number
	- The [[Maclaurin series]] of $\frac{1}{1 − x}$ is the [[geometric series]]:
	  logseq.order-list-type:: number
	  $$1+x+x^2+x^3+\cdots$$
	- By substituting $x$ for $1 − x$, the Taylor series of $\frac{1}{x}$ at $a = 1$ is
	  logseq.order-list-type:: number
	  $$1-(x-1)+(x-1)^2-(x-1)^3+\cdots$$
	- The [[Maclaurin series]] of $ln(1 − x)$([[natural logarithm]]) is
	  logseq.order-list-type:: number
	  $$-x-\frac{1}{2}x^2-\frac{1}{3}x^3-\frac{1}{4}x^4-\cdots$$
	- The corresponding Taylor series of $\ln x$ at $a=1$ is
	  logseq.order-list-type:: number
	  $$(x-1)-\frac{1}{2}(x-1)^2+\frac{1}{3}(x-1)^3-\frac{1}{4}(x-1)^4+\cdots$$
	  and more generally, the corresponding Taylor series of $ln x$ at an arbitrary **nonzero** point $a$ is
	  $$\ln a+\frac{1}{a}(x-a)-\frac{1}{a^2}\frac{(x-a)^2}{2}+\frac{1}{a^3}\frac{(x-a)^3}{3}-\frac{1}{a^4}\frac{(x-a)^4}{4}+\cdots$$
	- The Maclaurin series of the [[exponential function]] $e^x$([[Euler's number]]) is
	  logseq.order-list-type:: number
	  $$\sum_{n=0}^{\infty}\frac{x^n}{n!}=1+x+\frac{x^2}{2}+\frac{x^3}{3!}$$
	- The [[Maclaurin series]] of $\sin x$ is
	  logseq.order-list-type:: number
	  $$\sum_{n=0}^\infty \frac{(-1)^n}{(2n+1)!}x^{2n+1}=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$$
	- The [[Maclaurin series]] of $\cos x$ is
	  logseq.order-list-type:: number
	  $$\sum_{n=0}^\infty \frac{(-1)^n}{(2n)!}x^{2n}=x-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$$
- # Taylor series of complex function
	- ## Theorem
	  设函数 $f(z)$ 在简单闭曲线 $C$ 所围成的[[region]] $\text{D}$ 内[[解析]]。$f(z)$ 展开成[[泰勒级数]]：
	  $$f(z)=\sum_{n=0}^{\infty}\frac{f^{(n)}(z_0)}{n!}(z-z_0)^n$$
	  有：
	  $$\frac{f^{(n)}(z_0)}{n!}= \frac{1}{2\pi\mathrm{i}}\oint_{C}\frac{f(z)}{\left(z-z_0\right)^{n+1}}\mathrm{d}z$$
		- ## Corollary
			- f(z)在$z_0$[[解析]]$\Longleftrightarrow f(z)$在 $z_0$ [[邻域]]内能够 *展开* 成[[幂级数]]。
			  logseq.order-list-type:: number
	- > $f(z)=sum_{n=0}^{\infty}c_n(z-z_0)^n$[[收敛半径]]的求法：
	  找到与 $z_0$ *中心* 距离最近的[[奇点]]$a$，[[收敛半径]] $R=\left|z_0-a\right|$。
	- ## Example
		- The [[Maclaurin series]] of
		  logseq.order-list-type:: number
		  $$\ln(1+z)=z-\frac{z^{2}}{2}+\frac{z^{3}}{3}\cdots\frac{(-1)^{n-1}z^{n}}{n}+\cdots,\quad|z|<1$$
		- The [[Maclaurin series]] of
		  logseq.order-list-type:: number
		  $$\frac{1}{1-z}=\sum_{n=0}^{\infty}z^{n},\quad \left|z\right|<1$$
- ## [[多元函数泰勒展开]]
-