alias:: 傅里叶变换, FT, 傅氏变换

- ### 傅里叶变换的定义
  对于一个时间域函数 \(f(t)\)，其傅里叶变换 \(F(\omega)\) 定义为：
  $$F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-i\omega t} \, dt$$
  其中，\(\omega\) 是角频率，\(i\) 是虚数单位。
  $f(\omega)$ 也称为[[频谱函数]]。
- ### [[傅里叶逆变换]]
  傅里叶逆变换用于从频率域函数 \(F(\omega)\) 重构时间域函数 \(f(t)\)，定义为：
  $$f(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} F(\omega) e^{i\omega t} \, d\omega$$
- ## 推导
	- 傅里叶变换的详细数学推导是基于傅里叶级数的概念，将其扩展到非周期函数。这一过程涉及从离散到连续的过渡，让我们能够分析和表示在整个实数线上定义的函数的频率成分。以下是傅里叶变换的详细数学推导过程。
	- ### 从傅里叶级数到傅里叶变换
	  id:: 65d222bf-e52a-48f7-a1cd-dbb0f2d0337f
	  
	  1. **傅里叶级数回顾**：对于周期为 \(T\) 的周期函数 \(f(t)\)，其[[傅里叶级数]]表示为
	   $$f(t) = \sum_{n=-\infty}^{\infty} C_n e^{i 2\pi \frac{n}{T} t}$$
	   其中，\(C_n\) 是[[复数傅里叶系数]]，通过下式给出：
	   $$C_n = \frac{1}{T} \int_{-T/2}^{T/2} f(t) e^{-i 2\pi \frac{n}{T} t}\mathrm dt$$
	  2. **频率的连续化**：当我们处理[[非周期函数]]时，考虑周期 \(T\) 趋向于无穷大，使得频率 \(n/T\) 变得连续。定义 \(\Delta \omega = 2\pi / T\)，随着 \(T \rightarrow \infty\)，\(\Delta \omega \rightarrow d\omega\)，频率变为连续变量 \(\omega\)。
	  3. **傅里叶变换的引入**：在这个连续极限下，傅里叶级数转化为傅里叶变换。复数傅里叶系数 \(C_n\) 转化为傅里叶变换 \(F(\omega)\)，且求和转化为积分：
	  $$F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-i\omega t}\mathrm dt$$
	   这就是傅里叶变换，它提供了函数 \(f(t)\) 在频率 \(\omega\) 上的表示。
	  4. **傅里叶逆变换**：为了从频率域重构时域信号，我们需要傅里叶逆变换：
	   $$f(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} F(\omega) e^{i\omega t} d\omega$$
	   这表明时域函数可以通过其频域表示来完全重建。
		- > 参考[[傅里叶积分]]
		  【《积分变换》基础知识全解析，通信信号专业必学，适合0基础的同学快速学习】 【精准空降到 07:51】 https://www.bilibili.com/video/BV1wa4y1j7b1/?p=5&share_source=copy_web&vd_source=27f5502bd7a34d775a5d6aa446a54e99&t=471
	- ### 数学细节和假设
		- **局部可积**：\(f(t)\) 需要是局部可积的，以确保傅里叶变换存在。
		- **绝对可积**：如果 \(f(t)\) 是绝对可积的（即 \(\int_{-\infty}^{\infty} |f(t)| dt < \infty\)），则 \(F(\omega)\) 存在且连续。
- ## [[连续时间傅里叶变换]]
- ## [[离散时间傅里叶变换]]
- ## 定理
	- ### 1. 线性定理
	  傅里叶变换是线性的，这意味着对于任何两个函数 \(f(t)\) 和 \(g(t)\)，以及任何两个常数 \(a\) 和 \(b\)，都有：
	  $$\mathcal{F}\{a f(t) + b g(t)\} = a \mathcal{F}\{f(t)\} + b \mathcal{F}\{g(t)\}$$
	  > 本质上是源于积分的线性。
	- ### 2. [[时移定理]]
	  时移定理表明，如果 \(f(t)\) 的傅里叶变换是 \(F(\omega)\)，那么 \(f(t - t_0)\) 的傅里叶变换是 \(e^{-i\omega t_0} F(\omega)\)。这说明时间域的平移等价于频率域的 [[相位变换]] 。
	  $$\mathcal{F}\{f(t - t_0)\} = e^{-i\omega t_0} F(\omega)$$
	- ### 3. [[频移定理]]
	  频移定理说明，如果给定信号 \(f(t)\) 的傅里叶变换是 \(F(\omega)\)，那么 \(e^{i\omega_0 t}f(t)\) 的傅里叶变换是 \(F(\omega - \omega_0)\)。这表明频率域的平移对应于时域的调制。
	  $$\mathcal{F}\{e^{i\omega_0 t}f(t)\} = F(\omega - \omega_0)$$
	- ### 4. 缩放定理（[[相似性质]]）
	  如果有 \(f(at)\)（其中 \(a\) 是非零实数），那么其傅里叶变换是 \(\frac{1}{|a|}F\left(\frac{\omega}{a}\right)\)。这说明时域的缩放等价于频率域的反向缩放且伴随幅度的调整。
	  $$\mathcal{F}\{f(at)\} = \frac{1}{|a|} F\left(\frac{\omega}{a}\right)$$
	- ### 5. 实对称性
	- 如果原始信号是**实**数（不包含虚部），那么其频谱具有[[共轭对称性]]。即如果 \(F(\omega)\) 是 \(f(t)\) 的傅里叶变换，那么 
	  collapsed:: true
	  $$F(-\omega) = F^*(\omega),$$ 
	  其中 \(^*\) 表示复共轭。
		- 如果原始信号是偶函数，其频谱也是偶函数；如果原始信号是奇函数，其频谱是奇函数。
		- #### 复共轭定理
		  如果 \(f(t)\) 的傅里叶变换是 \(F(\omega)\)，那么 \(f^*(t)\)（\(f(t)\) 的[[复共轭]]）的傅里叶变换是 \(F^*(-\omega)\)。
		  
		  $$\mathcal{F}\{f^*(t)\} = F^*(-\omega)$$
	- ### 6. [[微分性质]]
		- 若  $\lim _{|t|\to+\infty} f(t)=0$ , 则
		  $$\mathcal{F}\left[f^{\prime}(t)\right]=\mathrm{j} \omega \mathcal{F}[f(t)],$$
		- 一般地, 若  $\lim _{|t|\to+\infty} f^{(k)}(t)=0(k=0,1,2, \cdots, n-1)$ , 则
		  $$\mathcal{F}\left[f^{(n)}(t)\right]=(\mathrm{j} \omega)^{n} \mathcal{F}[f(t)] .$$
		- > **证明**
		  【《积分变换》基础知识全解析，通信信号专业必学，适合0基础的同学快速学习】 【精准空降到 03:08】 https://www.bilibili.com/video/BV1wa4y1j7b1/?p=23&share_source=copy_web&vd_source=27f5502bd7a34d775a5d6aa446a54e99&t=188
		- 同样,还能得到 像函数 的导数公式为
		  $$\frac{\mathrm{d}}{\mathrm{d} \omega} F(\omega)=-\mathrm{j} \mathscr{F}[t f(t)],$$
		  一般地, 有
		  $$\frac{\mathrm{d}^{n} F(\omega)}{\mathrm{d} \omega^{n}}=(-\mathrm{j})^{n} \mathscr{F}\left[t^{n} f(t)\right] .$$
		  当  $f(t)$  的傅氏变换已知时, 上式可用来求  $t^{n} f(t)$  的傅氏变换：
		  $$
		  \mathcal F[t^{n}f(t)] = j^{n} \cdot F^{(n)}(\omega) $$
		- ### 例子
		  $$
		  \mathcal F[t]=\mathcal F[t\cdot 1]=j(2 \pi \delta(\omega))^{\prime}=j 2 \pi \delta^{\prime}(\omega) $$
		  $$\mathcal F\left[t^{n}\right]=j^{n} \cdot(2 \pi \delta(\omega)]^{(n)}=2 \pi j^{n} \cdot \delta^{(n)}(\omega) $$
			- 衰减函数
			  $$
			  f(t)=\left\{\begin{array}{ll}
			  0 & t < 0 \\
			  e^{-\beta t} & t \geqslant 0
			  \end{array}\right. $$
			  则
			  $$F(\omega)=\frac{1}{\beta+j \omega}$$
			  $$F\left[t f(t)\right]=j\left(\frac{1}{\beta+j \omega}\right)^{\prime}=\frac{1}{(\beta+j \omega)^{2}}$$
	- ### 7. 傅里叶变换的[[卷积定理]]
	  卷积定理是傅里叶变换中的一个关键性质，它表明两个函数在[[时域]]的卷积等价于它们的傅里叶变换在[[频域]]的乘积。
	  $$\mathcal{F}\{f(t) * g(t)\} = F(\omega)G(\omega)$$
	- ### 8. [[帕塞瓦尔定理]]
	  设  $F(\omega)=\mathcal{F}[f(t)]$ , 则有
	  $$\int_{-\infty}^{+\infty} f^{2}(t) \mathrm{d} t=\frac{1}{2 \pi} \int_{-\infty}^{+\infty}|F(\omega)|^{2} \mathrm{~d} \omega .$$
		- >【《积分变换》基础知识全解析，通信信号专业必学，适合0基础的同学快速学习】 【精准空降到 02:12】 https://www.bilibili.com/video/BV1wa4y1j7b1/?p=26&share_source=copy_web&vd_source=27f5502bd7a34d775a5d6aa446a54e99&t=132
	- ### 9. 双边拉普拉斯变换与傅里叶变换的关系
	  
	  傅里叶变换可以看作是[[双边拉普拉斯变换]]在\(s = i\omega\)（其中 \(s\) 是复频率参数）时的特殊情况。这一点揭示了傅里叶变换与更广泛的数学分析工具之间的联系，并帮助我们理解信号在复频域的行为。
	- ### 10. 积分性质
		- 设  $g(t)=\int_{-\infty}^{t} f(t) \mathrm{d} t$ , 若  $\lim _{t \rightarrow+\infty} g(t)=0$ , 则
		  $$\mathcal{F}[g(t)]=\frac{1}{\mathrm{j} \omega} \mathcal{F}[f(t)] =\frac{1}{j\omega}F(\omega).$$
		- 假设 \(f(t)\) 是一个时间域中的函数，其傅里叶变换为 \(F(\omega)\)。考虑 \(f(t)\) 在时域的积分 \(\int_{-\infty}^{t} f(\tau) d\tau\)，其傅里叶变换可以表示为：
		  $$\mathcal{F}\left\{\int_{-\infty}^{t} f(\tau) d\tau\right\} = \frac{1}{i\omega}F(\omega) + \pi F(0)\delta(\omega)$$
		  该表达式显示了时域积分在频域中对应于原频谱除以 \(i\omega\) 的效果，同时在 \(\omega = 0\) 处添加了一个与 \(F(0)\) 成比例的冲击。
- ## [[余弦变换]]
- ## [[正弦变换]]
- ## 特殊函数对应的傅里叶变换
	- 1. [[狄拉克δ函数]] $\delta(t)$
		- 傅里叶变换：$\mathcal{F}\{\delta(t)\} = 1$
		- **频谱**：这表示一个瞬时脉冲在所有频率上都有相同的幅度。
	- 2. **[[单位阶跃函数]]** $u(t)$
		- 傅里叶变换：$\mathcal{F}\{u(t)\} = \pi \delta(\omega) + \frac{1}{j\omega}$
		- **频谱**：阶跃函数在频域中包含一个无穷大的直流分量和一个随 $\omega$ 递减的分量。
	- 3. **[[实指数衰减函数]]** $e^{-at}u(t)$，其中 $a > 0$
		- 傅里叶变换：$\mathcal{F}\{e^{-at}u(t)\} = \frac{1}{a + j\omega}$
		- **频谱**：实指数衰减函数的傅里叶变换是一个复数，其幅度随 $\omega$ 的增加而减小。
	- 4. **[[正弦函数]]** $\sin(\omega_0 t)$
		- 傅里叶变换：$\mathcal{F}\{\sin(\omega_0 t)\} = j\frac{\pi}{2} [\delta(\omega - \omega_0) - \delta(\omega + \omega_0)]$
		- **频谱**：正弦波的傅里叶变换显示在 $\pm\omega_0$ 处有两个点，表示其频域中的频率成分。
	- 5. **[[余弦函数]]** $\cos(\omega_0 t)$
		- 傅里叶变换：$\mathcal{F}\{\cos(\omega_0 t)\} = \pi [\delta(\omega - \omega_0) + \delta(\omega + \omega_0)]$
		- **频谱**：余弦波的傅里叶变换也显示在 $\pm\omega_0$ 处有两个点，与正弦波类似，但没有虚数部分。
	- 6. **[[高斯函数]]** $e^{-a t^2}$，其中 $a > 0$
		- 傅里叶变换：$\mathcal{F}\{e^{-a t^2}\} = \sqrt{\frac{\pi}{a}}e^{-\frac{\omega^2}{4a}}$
		- **频谱**：高斯函数的频谱同样是一个高斯函数，形式为 \(F(\omega) = e^{-\omega^2/(4\pi)}\)。展示了时域和频域的对称性。
	- 7. **[[矩形脉冲函数]]** $\mathrm{rect}(t/T)$
		- 傅里叶变换：$\mathcal{F}\{\mathrm{rect}(t/T)\} = T \cdot \mathrm{sinc}(T\omega/2\pi)$
		- **频谱**：矩形脉冲的傅里叶变换是一个[[sinc 函数]]（ \(\text{sinc}(x) = \frac{\sin(\pi x)}{\pi x}\)），其宽度与脉冲宽度成反比。
-