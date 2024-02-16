alias:: 切比雪夫级数

- ## 定义
	- 如果 $f(x){\in}C[-1,1]$ , 按 $\{ T_k(x)\}_0^{\infty}$ 展成[[广义傅里叶级数]]（其中 $T_k(x)$ 是[[第一类切比雪夫多项式]]），可得级数
	  $$
	  \frac{C_0^*}2+\sum_{k\operatorname{=}1}^\infty C_k^*T_k(x)\:, \tag{1}
	  $$
	  称为 $f(x)$ 在 $[-1，1]$ 上的[[切比雪夫级数]].
	  > $f(x)$ 可以用切比雪夫多项式的[[无穷级数]]来逼近它。
	- 其中系数 $C_0^*$ 由下式得到
	  $$
	  C_k^*\:=\frac{2}{\pi}\int_{-1}^1\frac{f(x)\:T_k(x)}{\sqrt{1-x^2}}\:\mathrm{d}x,\quad k=0,1,\cdots,
	  $$
	  这里
	  $$
	  T_k(x)\:=\:\cos(k\text{arccos }x)\:,\quad\mid x\mid\leqslant1.
	  $$
	- 若令 $x=\cos\theta,0\leqslant\theta\leqslant\pi$, 则 $(1)$ 式就是 $f(\cos\theta)$ 的[[傅里叶级数]]，其中
	  $$
	  C_k^*=\frac2\pi\!\int_0^\pi f(\cos\theta)\cos k\theta\:\mathrm{d}\theta,\quad k=0,1,\cdotp\cdotp.
	  $$
	  于是根据傅里叶级数理论知，只要 $f^{\prime\prime}(x)$在 $[-1,1]$ 上[[分段连续]]，则 $f(x)$在 $[-1,1]$ 上的切比雪夫级数[[一致收敛]]于 $f(x)$ .
	- 从而可表示为
	  $$
	  f(x)=\frac{C_0^*}2+\sum_{k=1}^\infty C_k^*\:T_k\left(x\right),
	  $$
	  取它的部分和
	  $$
	  C_n^*\left(x\right)=\frac{C_0}2+\sum_{k=1}^nC_k^*T_k\left(x\right),
	  $$
	  其误差为
	  $$
	  f(x)-C_n^*\left(x\right)\approx C_{n+1}^*T_{n+1}\left(x\right).
	  $$
	  一致收敛意味着：级数的部分和 \( C_n^*(x) \) 与函数 \( f(x) \) 之间的最大误差，对于所有的 \( x \) 来说，随着 \( n \) 的增加而减小，并且最终小于任意给定的正数 \( \varepsilon \)。换句话说，随着 \( n \) 的增加，\( C_n^*(x) \) 在整个区间 \([-1, 1]\) 上[[均匀地逼近]] \( f(x) \) 。$T_{n+1}(x)$ 的最大值 $\max_{-1\leq x\leq1}|T_{n+1}(x)|$ 最小（[[切比雪夫多项式]]的[[最大误差]]在逼近区间内的振幅是最小的），因此 $C_n^*(x)$ 可作为 $f(x)$ 在 $[-1,1]$ 上的 *近似[[最佳一致逼近多项式]]* 。