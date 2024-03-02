alias:: 狄拉克δ函数, 单位脉冲函数, unit impulse function, δ函数, 单位冲击函数

- 单位脉冲函数（Unit Impulse Function），在数学和信号处理领域中，是一个非常重要的概念。它通常被表示为 $\delta(t)$，
  $$\delta(t) = 
     \begin{cases} 
     \infty, & \text{for } t = 0 \\
     0, & \text{for } t \neq 0 
     \end{cases}$$
  其中 $t$ 是时间变量。
- ## 性质
	- **无限小宽度与无限大的高度**：理想的单位脉冲函数在 $t = 0$ 时具有无限大的幅值，在其他时间点的幅值为0。尽管这在物理世界中无法实现，但它在数学上是一个非常有用的抽象概念。
	- **单位面积**：尽管 $\delta(t)$ 在 $t = 0$ 时的值无限大，在其他时间点的值为0，但它的总积分值（或面积）被定义为1。这可以表示为：
	     $$
	     \int_{-\infty}^{\infty} \delta(t) \,\mathrm dt = 1
	     $$
	- **[[筛选性质]]**（Sifting Property）：单位脉冲函数具有筛选任何连续函数 $f(t)$ 在 $t = 0$ 点值的特性，这表示为：
	     $$
	     \int_{-\infty}^{\infty} f(t) \delta(t) \,\mathrm dt = f(0)
	     $$
		- δ函数也可以“提取”出在其不为零处的函数值：
		     $$\int_{-\infty}^{\infty} f(t) \delta(t - a) \, dt = f(a)$$
	- $\delta(t)$ 是 偶函数 。
	- $$\int_{-\infty}^{+\infty} f(t) \delta^{\prime}(t)\mathrm d t=-f^{\prime}(0)$$
		- ### 证明
			- $$\begin{aligned}
			  \int_{-\infty}^{+\infty} f(t) \delta^{\prime}(t)\mathrm d t=\int_{-\infty}^{+\infty} f(t)\mathrm d \delta(t)&=\left.f(t) \cdot \delta(t)\right|_{-\infty} ^{+\infty}-\int_{-\infty}^{+\infty} \delta(t) \cdot f'(t)\mathrm d t \\
			  &=0-f'(0) \\
			  &=-f'(0)
			  \end{aligned}$$
		- $n$ 阶导数同样成立。
- 在离散时间信号处理中，单位脉冲函数的离散等价物是[[单位脉冲序列]] $\delta[n]$ 。
- ## 单位脉冲函数的傅里叶变换
	- 对于单位脉冲函数 $\delta(t)$，其傅里叶变换表达式相对简单。单位脉冲函数的傅里叶变换是一个常数，具体表达式如下：
	  $$\mathcal{F}[\delta(t)]=\int_{-\infty}^{+\infty} \delta(t) \mathrm{e}^{-\mathrm{j} \omega t} \mathrm{~d} t=\left.\mathrm{e}^{-\mathrm{j} \omega t}\right|_{t=0}=1 .$$
	- > 这个结果的物理意义非常深远。它表明，一个理想的单位脉冲函数**包含了所有频率的成分，且各频率成分的幅度相同**，称此为[[均匀频谱]]。这是因为单位脉冲函数是非常短暂的，理论上瞬时地将能量传递给系统，因此它能够激发系统中所有可能的频率响应。
	- $$\mathcal{F}\left[1\right]=\int_{-\infty}^{+\infty} \mathrm{e}^{-\mathrm{j} \omega t} \mathrm{d} t=\int_{-\infty}^{+\infty} \mathrm{e}^{\mathrm{j} \omega \tau} \mathrm{d} \tau=2 \pi \delta(\omega)$$
		- ### 证明
		  \begin{aligned}
		  F^{-1}[2 \pi \delta(\omega)]&=\frac{1}{2 \pi} \int_{-\infty}^{+\infty} 2 \pi \delta(\omega) \cdot e^{j \omega{t}} \cdot d \omega \\
		  &=\left.e^{j \omega t}\right|_{\omega=0}=1
		  \end{aligned}
		- $$
		  \int_{-\infty}^{+\infty} \mathrm{e}^{-\mathrm{j} \omega t} \mathrm{d} t=\int_{-\infty}^{+\infty}(\cos \omega t-j \sin \omega t) \mathrm d t=\int_{-\infty}^{+\infty} \cos \omega t \mathrm d t=2 \pi \delta(\omega)
		  $$
	- id:: 65d9fdb4-a52e-4e85-93ea-ba084da0be18
	  $$\mathcal{F}\left[e^{-jw_0t}\right]=\int_{-\infty}^{+\infty} \mathrm{e}^{\mathrm{j} \omega_0  t} \mathrm{e}^{-\mathrm{j} \omega t} \mathrm{~d} t=\int_{-\infty}^{+\infty} \mathrm{e}^{\mathrm{j}\left(\omega_{0}-\omega\right) t} \mathrm{~d} t=2 \pi \delta\left(\omega_{0}-\omega\right)=2 \pi \delta\left(\omega-\omega_{0}\right) .$$
-