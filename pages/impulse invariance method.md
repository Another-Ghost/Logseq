alias:: 脉冲响应不变法

- 脉冲响应不变法是一种将模拟滤波器转换为数字滤波器的技术，目的是在离散时间实现中保持模拟滤波器的脉冲响应特性。这种方法尤其适用于那些脉冲响应对系统性能至关重要的应用，如在信号处理和控制系统中。下面是使用脉冲响应不变法设计数字滤波器的逐步过程：
- ### 步骤 1: 确定模拟滤波器的脉冲响应
	- **选择模拟滤波器**：首先，选择一个满足设计要求的模拟滤波器。这可以是一个低通、高通、带通或带阻滤波器。
	  logseq.order-list-type:: number
	- **计算脉冲响应**：计算所选模拟滤波器的脉冲响应 \(h_a(t)\)。脉冲响应是滤波器对冲激输入 \( \delta(t) \) 的响应。
	  logseq.order-list-type:: number
- ### 步骤 2: 离散化模拟滤波器的脉冲响应
	- **采样脉冲响应**：以固定的采样率 \( F_s \) 对模拟滤波器的脉冲响应 \(h_a(t)\) 进行采样，得到离散时间脉冲响应 \(h[n]\)。采样间隔 \(T = 1/F_s\)。
	  logseq.order-list-type:: number
	  \[ h[n] = h_a(nT) \]
	- **注意混叠**：在采样过程中，需要注意防止混叠现象，确保采样率足够高，以准确捕获模拟滤波器的脉冲响应特性。
	  logseq.order-list-type:: number
- ### 步骤 3: 应用Z变换
	- **Z变换**：对离散时间脉冲响应 \(h[n]\) 应用Z变换，得到数字滤波器的Z域传递函数 \(H(z)\)。
	  $$H(z) = \mathcal{Z}\{h[n]\}$$
	- $H_{a}(s)$ 转换成 $H(z)$ 的实用公式
	  $$H(z)=\sum_{i=1}^{N} \frac{T A_{i}}{1-e^{S_{i} T} z^{-1}}$$
	  说明：
		- $e^{s_iT}$ 是 $H_{a}(s)$ 中每个 $s$ 域极点转换成 $z$ 域极点
		  logseq.order-list-type:: number
		- $A_{i}$ 是 $H_{a}(s)$ 部分分式展开的各项系数
		  logseq.order-list-type:: number
		- 由基本 $z$ 变换对 
		  logseq.order-list-type:: number
		  $$\frac{1}{1-a z^{-1}} \leftrightarrow a^{n} u(n)$$ 
		  可知
		  $$\frac{1}{1-e^{s_{i} T} z^{-1}} \leftrightarrow e^{s_{i} T n} u(n)$$
		  （因为从连续域到离散域一直是[[单位脉冲响应]]，原函数的形式保持不变，所以称为脉冲响应不变法）
		- $\mathrm{T}$ 是[[采样间隔]]，其作用在于避免当 $\mathrm{T}$ 过小时 $\left|\mathrm{H}\left(e^{j \omega}\right)\right|$ 值过大，如无特殊说明，可以取 $1$
		  logseq.order-list-type:: number
			- 由于是对连续系统的单位冲激响应采样，即有：
			  $$\hat{h}_{a}(t)=\sum_{n=-\infty}^{+\infty} h_{a}(n T) \delta(t-n T)$$
			  对应的傅里叶变换关系为 
			  $$H\left(e^{j \omega}\right)=\frac{1}{T} \sum_{n=-\infty}^{\infty} H_{a}\left(\frac{j \omega-2 \pi k}{T}\right)$$
- ### 步骤 4: 处理预畸变
	- **频率预畸变**：脉冲响应不变法不会引入预畸变处理步骤，因为该方法直接保持了模拟滤波器的脉冲响应特性。不过，这种方法可能导致频率响应的变化，特别是在高频部分。
	  logseq.order-list-type:: number
- ### 步骤 5: 实现数字滤波器
	- **确定差分方程**：根据 \(H(z)\) 的表达式，确定对应的差分方程。这个方程描述了数字滤波器在每个时间步的输入和输出之间的关系。
	  logseq.order-list-type:: number
	- **编程实现**：使用适当的编程语言或软件（如MATLAB、Python等）根据差分方程实现数字滤波器。
	  logseq.order-list-type:: number
- ### 步骤 6: 验证和测试
	- **验证性能**：通过软件模拟，验证数字滤波器的性能是否符合设计要求，特别是其脉冲响应和频率响应。
	  logseq.order-list-type:: number
	- **调整和优化**：如果需要，根据测试结果调整设计参数，优化滤波器性能。
	  logseq.order-list-type:: number
- ## 例子
	- ((66163c65-1233-4f02-95eb-b727f383cd11))