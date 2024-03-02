alias:: 复变量函数, 复变函数, 复变量

- 设 $D$ 是[[complex plane]]上一*点集*，如果对于 $D$ 中任意的一点$z$,有确定的[[复数]]$w$同它对应，则称在 $D$ 上定义了一个[[complex function]],记作 
  id:: 649be53c-fa5d-4254-ac57-32cb5822b946
  $$w=f(z)$$
- 如果对每个 $z\in D$, 有唯一的 $w$ 同它对应，则称 $w=f(z)$ 为[[单值函数]]；
- 不是[[单值函数]]的函数称为[[多值函数]]。
- 若 $D$ 是[[实轴]]上的一个[[闭区间]]，则 $w=f(z)$ 就是[[实变量的复值函数]].
	- [[曲线的参数方程]] $z=z\left(t\right)\ (a≤1≤b$ 就是这种函数的一个例子。
- 设$z=x+iy$，则$w=f(z)$可以写成下列形式:
  $$
  w=f(z)=u+\mathrm{i}v=u(x,y)+\mathrm{i}v(x,y)
  $$
  其中 $u\left(x,y\right)$ 与 $v\left(x,y\right)$ 为[[实值函数]].分开上式的[[实部]]与[[虚部]]，得到
  $$u = u(x,y), D =v(x,y)$$
  这样，一个[[complex function]] $w=f(z)$ 就相当于一对*二元*[[实变函数]].
	- > $w=f(z)$的性质就取决于 $u=u\left(x,y\right)$ 与$v=v\left(\begin{matrix}x,y\end{matrix}\right)$ 的性质。
- # [[复变函数]]与[[实变函数]]
	- 不同点：
	  logseq.order-list-type:: number
		- $e^z$是 *周期函数* ，*周期* 为 $2k\pi i\ (k=0,\pm 1, \pm 2,\cdots)$。
		  logseq.order-list-type:: number
		- $\ln(-1)=i\pi$，$\operatorname{Ln} z= \ln z + 2k\pi i\ (i=0,\pm 1\pm 2,\cdots)$
		  logseq.order-list-type:: number
		- $\operatorname{Ln} z^2\ne 2\operatorname{Ln}z$。
		  logseq.order-list-type:: number
		- $1^{\sqrt{2}}\ne 1$ 有 *无穷* 多个值。
		  logseq.order-list-type:: number
		- $\sin z, \cos$是 *无界* 的。
		  logseq.order-list-type:: number
		- $\sqrt[3]{-27}$是三个值。
		  logseq.order-list-type:: number
-