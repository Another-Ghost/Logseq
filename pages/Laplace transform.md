alias:: 拉普拉斯变换, 拉氏变换

- 设函数  $f(t)$  是定义在  $[0,+\infty)$  上的 实值函数 , 如果对于复参数  $s=\beta+\mathrm{j} \omega$ , 积分
  $$F(s)=\int_{0}^{+\infty} f(t) \mathrm{e}^{-s t} \mathrm{d} t \tag{1}$$
  在[[复平面]]  $s$  的某一[[区域]]内[[收敛]],则称  $F(s)$  为  $f(t)$  的 *拉普拉斯变换* , 记为  $F(s)=\mathcal{L}[f(t)]$ ; 
  相应地, 称  $f(t)$  为  $F(s)$  的[[拉普拉斯逆变换]], 记为  $f(t)=\mathcal{L}^{-1}[F(s)]$ . 有时也称  $f(t)$  与  $F(s)$  分别为[[像原函数]]和[[像函数]].
- ### 拉普拉斯变换与傅里叶变换的关系
	- 由 $(1)$ 式有
	  \begin{aligned}
	  \mathcal{L}[f(t)] & =\int_{0}^{+\infty} f(t) \mathrm{e}^{-s t} \mathrm{~d} t=\int_{0}^{+\infty} f(t) \mathrm{e}^{-\beta t} \cdot \mathrm{e}^{-\mathrm{j} \omega t} \mathrm{~d} t \\
	  & =\int_{-\infty}^{+\infty} f(t) u(t) \mathrm{e}^{-\beta t} \mathrm{e}^{-\mathrm{j} \omega t} \mathrm{~d} t=\mathcal{F}\left[f(t) u(t) \mathrm{e}^{-\beta t}\right] .
	  \end{aligned}
	  可见函数  $f(t)$  的拉氏变换就是  $f(t) u(t) \mathrm{e}^{-\beta t}$  的[[傅氏变换]].
	- 其基本想法是: 首先通过[[单位阶跃函数]]  $u(t)$  使函数  $f(t)$  在  $t<0$  的部分充零 (或者补零); 
	  其次对函数  $f(t)$  在  $t>0$  的部分乘上一个[[衰减指数函数]]  $\mathrm{e}^{-\beta t}$  以降低其 “增长” 速度, 这样就有希望使函数  $f(t) u(t) \mathrm{e}^{-\beta t}$  满足[[傅里叶积分条件]], 从而对它进行傅氏积分.
- ### [[拉普拉斯变换存在定理]]
	- 设函数  $f(t)$  满足:
		- 在  $t \geqslant 0$  的任何[[有限]]区间上[[分段连续]];
		  logseq.order-list-type:: number
		- 当  $t \rightarrow+\infty$  时,  $f(t)$  具有 有限的增长性 , 即存在常数  $M>0$  及  $c$ , 使得
		  logseq.order-list-type:: number
		  $$|f(t)| \leqslant M \mathrm{e}^{c t} \quad(0 \leqslant t<+\infty)$$
	- 其中  $c$  称为  $f(t)$  的[[增长指数]]. 则 像函数  $F(s)$  在[[半平面]]  $\operatorname{Re} s>c$  上一定存在, 且是[[解析]]的.
	- >如果一个函数, 即使它的绝对值随着  $t$  的增大而增大, 但只要不比某个指数函数增长得快, 则它的拉氏变换存在,这可以从拉氏变换与傅氏变换的关系中得到一种直观的解释. 常见的大部分函数都是满足的, 如三角函数、指数函数以及幂函数等. 而函数  $\mathrm{e}^{t^{2}}$  则不满足, 因为无论取多大的  $M$  与  $c$ , 对足够大的  $t$ , 总会出现  $\mathrm{e}^{t^{2}}>M \mathrm{e}^{c t}$ , 因此其拉氏变换不存在. 但必须注意的是, 定理的条件是充分的, 而不是必要的。
- ## 常见函数的拉普拉斯变换
	- **[[单位阶跃函数]]** \( u(t) \)
	   $$\mathcal{L}\{u(t)\} = \frac{1}{s}, \quad \text{Re}(s) > 0$$
	- **[[单位冲击函数]]** \( \delta(t) \)
	   $$\mathcal{L}\{\delta(t)\} = 1$$
	- **[[指数函数]]** \( e^{at} \)
	   $$\mathcal{L}\{e^{at}\} = \frac{1}{s-a}, \quad \text{Re}(s) > a$$
	- **[[正弦函数]]** \( \sin(bt) \)
	   $$\mathcal{L}\{\sin(bt)\} = \frac{b}{s^2 + b^2}, \quad \text{Re}(s) > 0$$
	- **[[余弦函数]]** \( \cos(bt) \)
	   $$\mathcal{L}\{\cos(bt)\} = \frac{s}{s^2 + b^2}, \quad \text{Re}(s) > 0$$
	- **t 的[[幂函数]]** \( t^n \) (n为正整数)
	   $$\mathcal{L}\{t^n\} = \frac{n!}{s^{n+1}}, \quad \text{Re}(s) > 0$$
	  > [[伽玛函数]]
	- **指数衰减正弦函数** \( e^{at} \sin(bt) \)
	   $$\mathcal{L}\{e^{at} \sin(bt)\} = \frac{b}{(s-a)^2 + b^2}, \quad \text{Re}(s) > a$$
	- **指数衰减余弦函数** \( e^{at} \cos(bt) \)
	   $$\mathcal{L}\{e^{at} \cos(bt)\} = \frac{s-a}{(s-a)^2 + b^2}, \quad \text{Re}(s) > a$$
- ### 周期函数的拉普拉斯变换
	- 周期函数的拉普拉斯变换是分析和处理周期性信号或系统时的一个重要工具。对于一个周期为 \(T\) 的周期函数 \(f(t)\)，其拉普拉斯变换可以通过以下公式计算：
	  $$
	  \mathcal{L}\{f(t)\} = \frac{1}{1 - e^{-sT}} \int_{0}^{T} e^{-st} f(t) \, dt
	  $$
	  这里，\(s\) 是复频域变量。
	- ### 解释
	  
	  该公式的含义是，周期函数的拉普拉斯变换可以通过计算函数在一个周期内的拉普拉斯变换，然后除以 \(1 - e^{-sT}\) 来得到。这样做的原因是周期函数可以看作是在每个周期上重复的函数序列的叠加，而 \(1 - e^{-sT}\) 正好反映了这种无限叠加的效应。
	- ### 示例
	  
	  假设有一个周期函数 \(f(t)\)，其周期 \(T = 2\)，并且在一个周期内的表达式为 \(f(t) = t\) （对 \(0 \leq t < 2\)）。我们要计算这个函数的拉普拉斯变换。
	  
	  根据公式，我们首先计算一个周期内的拉普拉斯变换：
	  
	  \[
	  \int_{0}^{T} e^{-st} t \, dt = \int_{0}^{2} e^{-st} t \, dt
	  \]
	  
	  进行积分得到：
	  
	  \[
	  \left[ -\frac{t}{s}e^{-st} \right]_{0}^{2} + \frac{1}{s} \int_{0}^{2} e^{-st} \, dt = -\frac{2}{s}e^{-2s} + \frac{1}{s^2}(1 - e^{-2s})
	  \]
	  
	  然后，将其代入周期函数的拉普拉斯变换公式中：
	  
	  \[
	  \mathcal{L}\{f(t)\} = \frac{1}{1 - e^{-2s}} \left( -\frac{2}{s}e^{-2s} + \frac{1}{s^2}(1 - e^{-2s}) \right)
	  \]
	  
	  这个表达式给出了给定周期函数的拉普拉斯变换。
- ## 拉普拉斯变换的性质
	- [[线性性质]]
	  logseq.order-list-type:: number
	  设  $\alpha$, $\beta$  为常数, 且有  $\mathcal{L}[f(t)]=F(s)$, $\mathcal{L}[g(t)]=G(s)$ , 则有
	  \begin{aligned}
	  \mathscr{L}[\alpha f(t)+\beta g(t)] & =\alpha F(s)+\beta G(s), \\
	  \mathscr{L}^{-1}[\alpha F(s)+\beta G(s)] & =\alpha f(t)+\beta g(t) .
	  \end{aligned}
	- [[相似性质]]
	  logseq.order-list-type:: number
	  设  $\mathcal{L}[f(t)]=F(s)$ , 则对任一常数  $a>0$  有
	  $$\mathcal{L}[f(a t)]=\frac{1}{a} F\left(\frac{s}{a}\right) .$$
	- [[时延性质]]（Time Shifting）
	  logseq.order-list-type:: number
	  $$\mathcal{L}\{f(t - a)u(t - a)\} = e^{-as}F(s)$$
	  对函数\(f(t)\)的拉普拉斯变换延迟\(a\)秒得到的结果是原变换乘以\(e^{-as}\)。
	- [[频移性质]]（Frequency Shifting）
	  logseq.order-list-type:: number
	  $$\mathcal{L}\{e^{at}f(t)\} = F(s - a)$$
	  如果在时间域的函数乘以一个指数项，其拉普拉斯变换等于将原变换的 \(s\) 替换为 \(s-a\) 。
	- [[微分性质]]
	  logseq.order-list-type:: number
		- [[导数]]的像函数
		  logseq.order-list-type:: number
			- 设  $\mathcal{L}[f(t)]=F(s)$ , 则有
			  $$\mathcal{L}\left[f^{\prime}(t)\right]=s F(s)-f(0) ;$$
			- 一般地,有
			  $$\mathcal{L}\left[f^{(n)}(t)\right]=s^{n} F(s)-s^{n-1} f(0)-s^{n-2} f^{\prime}(0)-\cdots-f^{(n-1)}(0),$$
			  其中,  $f^{(k)}(0)$  应理解为  $\lim _{t \rightarrow 0^{+}} f^{(k)}(t)$ .
			- >拉氏变换的这一性质可用来求解[[常微分方程的初值问题]]。
		- 像函数的导数
		  logseq.order-list-type:: number
			- 设  $\mathcal{L}[f(t)]=F(s)$ , 则有
			  $$F^{\prime}(s)=-\mathcal{L}[t f(t)],$$
			- 一般地,有
			  $$F^{(n)}(s)=(-1)^{n} \mathcal{L}\left[t^{n} f(t)\right] .$$
				- > 例子 【《积分变换》基础知识全解析，通信信号专业必学，适合0基础的同学快速学习】 【精准空降到 06:45】 https://www.bilibili.com/video/BV1wa4y1j7b1/?p=41&share_source=copy_web&vd_source=27f5502bd7a34d775a5d6aa446a54e99&t=405
	- [[积分性质]]
	  logseq.order-list-type:: number
		- [[积分]]的像函数
		  logseq.order-list-type:: number
			- 设  $\mathscr{S}[f(t)]=F(s)$ , 则有
			  $$\mathcal{L}\left[\int_{0}^{t} f(t) \mathrm{d} t\right]=\frac{1}{s} F(s) ;$$
			- 一般地,有
			  $$\mathcal{L}\left[\int_{0}^{t} \mathrm{~d} t \int_{0}^{t} \mathrm{~d} t \cdots \int_{0}^{t} f(t) \mathrm{d} t\right]=\frac{1}{s^{n}} F(s) .$$
			  ($n$ 重积分)
		- 像函数的积分
		  logseq.order-list-type:: number
			- 设  $\mathcal{L}[f(t)]=F(s)$ , 则有
			  $$\int^{+\infty}_s F(s) \mathrm{d} s=\mathcal{L}\left[\frac{f(t)}{t}\right] = \int_{0}^{+\infty} \frac{f(t)}{t} e^{-s t}\mathrm d t,$$
				- $s=0$ 时有
				  $$\int_{0}^{+\infty} \frac{f(t)}{t}\mathrm d t=\int_{0}^{+\infty} F(s)\mathrm d s .$$
			- 一般地, 有
			  $$\int_{s}^{+\infty} \mathrm{d} s \int_{s}^{+\infty} \mathrm{d} s \cdots \int_{s}^{+\infty} F(s) \mathrm{d} s=\mathcal{L}\left[\frac{f(t)}{t^{n}}\right] .$$
			  ($n$ 重积分)
			- > 例子 【《积分变换》基础知识全解析，通信信号专业必学，适合0基础的同学快速学习】 【精准空降到 05:55】 https://www.bilibili.com/video/BV1wa4y1j7b1/?p=42&share_source=copy_web&vd_source=27f5502bd7a34d775a5d6aa446a54e99&t=355
- ## 卷积
	- 两个函数的卷积是指
	  $$f_{1}(t) * f_{2}(t)=\int_{-\infty}^{+\infty} f_{1}(\tau) f_{2}(t-\tau) \mathrm{d} \tau .$$
	  如果  $f_{1}(t)$  与  $f_{2}(t)$  满足当  $t<0$  时,  $f_{1}(t)=f_{2}(t)=0$ , 则有
	  $$\int_{-\infty}^{+\infty} f_{1}(\tau) f_{2}(t-\tau) \mathrm{d} \tau=\int_{0}^{+\infty} f_{1}(\tau) f_{2}(t-\tau) \mathrm{d} \tau=\int_{0}^{t} f_{1}(\tau) f_{2}(t-\tau) \mathrm{d} \tau .$$
	  此时两个函数的[[卷积]]为
	  $$f_{1}(t) * f_{2}(t)=\int_{0}^{t} f_{1}(\tau) f_{2}(t-\tau) \mathrm{d} \tau \quad(t \geqslant 0) .$$
	  >显然,由上式定义的卷积仍然满足交换律、结合律以及分配律等性质.
	- ### 拉普拉斯变换的[[卷积定理]]
		- 设  $\mathcal{L}\left[f_{1}(t)\right]=F_{1}(s), \mathcal{L}\left[f_{2}(t)\right]=F_{2}(s)$ , 则有  
		  $$\mathcal{L}\left[f_{1}(t) * f_{2}(t)\right]=F_{1}(s) \cdot F_{2}(s) .$$
		  $$f_{1}(t) * f_{2}(t)=\mathcal L^{-1}[F_{1}(s) \cdot F_{2}(s)] .$$
- ## 拉普拉斯变换的应用
	- ### 求解微分方程
		- 拉普拉斯变换是解决线性微分方程特别是[[常微分方程]]的一个强大工具。通过将时间域的微分方程转换为复频域的代数方程，拉普拉斯变换简化了求解过程。下面是一个基本步骤示例，演示如何使用拉普拉斯变换求解一个简单的微分方程。
		- ### 微分方程示例
		  考虑二阶常系数线性微分方程：
		  \[ y'' + ay' + by = f(t) \]
		  其中，\(y\)是未知函数，\(a\)和\(b\)是常数，\(f(t)\)是已知的输入函数。
		- ### 求解步骤
			- 1. **应用拉普拉斯变换**
			   对方程的每一项应用拉普拉斯变换，利用拉普拉斯变换的性质，特别是对导数的变换性质：
			- \( \mathcal{L}\{y'(t)\} = sY(s) - y(0) \)
			- \( \mathcal{L}\{y''(t)\} = s^2Y(s) - sy(0) - y'(0) \)
			  其中，\(Y(s)\)是\(y(t)\)的拉普拉斯变换，\(s\)是复频域变量。
			- 2. **代入拉普拉斯变换**
			  代入得到的拉普拉斯变换，得到一个关于\(Y(s)\)的代数方程：
			  \[ s^2Y(s) - sy(0) - y'(0) + a[sY(s) - y(0)] + bY(s) = F(s) \]
			  其中，\(F(s)\)是\(f(t)\)的拉普拉斯变换。
			- 3. **解代数方程**
			  将方程重写为\(Y(s)\)的表达式：
			  \[ Y(s) = \frac{F(s) + sy(0) + y'(0) + ay(0)}{s^2 + as + b} \]
			- 4. **应用逆拉普拉斯变换**
			  使用逆拉普拉斯变换将\(Y(s)\)转换回时间域，得到\(y(t)\)的表达式。
-