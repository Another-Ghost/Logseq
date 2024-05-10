## 线性相位 FIR 数字滤波器
	- 对于长度为 $N$ 的 $h(n)$ ，频率响应函数为
	  $$
	  H\left(\mathrm{e}^{\mathrm{j} \omega}\right)=\sum_{n=0}^{N-1} h(n) \mathrm{e}^{-\mathrm{j} \omega n}\tag{1}$$
	  $$
	  H\left(\mathrm{e}^{\mathrm{j} \omega}\right)=H_{\mathrm{g}}(\omega) \mathrm{e}^{\mathrm{j} \theta(\omega)}\tag{2}
	  $$
	  式中， $H_{\mathrm{g}}(\omega)$ 称为[[幅度特性]]； $\theta(\omega)$ 称为[[相位特性]]。
		- 注意，这里 $H_{\mathrm{g}}(\omega)$ 不同于 $\left|H\left(\mathrm{e}^{\mathrm{j} \omega}\right)\right|$ ， $H_{\mathrm{g}}(\omega)$ 为 $\omega$ 的实函数，可能取负值，而 $\left|H\left(\mathrm{e}^{\mathrm{j} \omega}\right)\right|$ 总是正值。
	- ^^线性相位 FIR 滤波器^^是指[[相位特性]] $\theta(\omega)$ 是 $\omega$ 的[[线性函数]]，即
	   $$\theta(\omega)=-\tau \omega \quad \tau\text{为常数}\tag{3}$$ 
	  如果 $\theta(\omega)$ 满足下式：
	  $$\theta(\omega)=\theta_{0}-\tau \omega \quad \theta_{0}\text{是起始相位}\tag{4}$$ 
	  严格地说，此时 $\theta(\omega)$ 不具有线性相位特性，但以上两种情况都满足[[群时延]]是一个常数，即
	  $$-\frac{\mathrm{d} \theta(\omega)}{\mathrm{d} \omega}=\tau$$
	  也称这种情况为[[线性相位]]。
	- 一般称满足 $(3)$ 式是[[第一类线性相位]]（严格线性相位特性）；满足 $(4)$ 式为[[第二类线性相位]]。
	  $\theta_{0}=-\pi / 2$ 是第二类线性相位特性常用的情况，所以本章仅介绍这种情况。
- ### 分类
	- 按[[时域约束条件]]分
		- [[第一类线性相位滤波器]]
		  logseq.order-list-type:: number
		  条件：
			- $\mathrm{h}(n)$ 为实序列
			  logseq.order-list-type:: number
			- 满足 $h(n)=h(N-1-n)$ 
			  logseq.order-list-type:: number
		- [[第二类线性相位滤波器]]
		  logseq.order-list-type:: number
		  条件：
			- $\mathrm{h}(n)$ 为实序列
			  logseq.order-list-type:: number
			- 满足 $h(n)=-h(N-1-n)$
			  logseq.order-list-type:: number
	- ### 例子
		- ((6617e10d-5ee2-4388-b5bc-4b03dacc2160))