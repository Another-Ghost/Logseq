alias:: 切比雪夫级数

- ## 定义
	- 如果 $f(x){\in}C[-1,1]$ , 按[[切比雪夫多项式]]族 $\{ T_k(x)\}_0^{\infty}$ 展成[[广义傅里叶级数]]，可得级数
	  $$
	  \frac{C_0^*}2+\sum_{k\operatorname{=}1}^\infty C_k^*T_k(x)\:, \tag{1}
	  $$
	  称为 $f(x)$ 在 $[-1，1]$ 上的[[切比雪夫级数]].
	  其中系数由下式得到
	  $$
	  C_k^*\:=\frac{2}{\pi}\int_{-1}^1\frac{f(x)\:T_k(x)}{\sqrt{1-x^2}}\:\mathrm{d}x,\quad k=0,1,\cdots,
	  $$
	  这里
	  $$
	  T_k(x)\:=\:\cos(k\text{arccos }x)\:,\quad\mid x\mid\leqslant1.
	  $$
	- 若令 $x=\cos\theta,0\leqslant\theta\leqslant\pi$, 则 $(1)$ 式就是 $f(\cos\theta)$ 的[[傅里叶级数]]，其中
	- $$
	  C_k^*=\frac2\pi\!\int_0^\pi f(\cos\theta)\cos k\theta\:\mathrm{d}\theta,\quad k=0,1,\cdotp\cdotp.
	  $$
	  于是根据傅里叶级数理论知，只要 $f^{\prime\prime}(x)$在 $[-1,1]$ 上[[分段连续]]，则 $f(x)$在[-1,1]上的切比雪夫级数(3,16)一致收敛于 $f(x)$.从而可表示为
	- $$
	  f(x)=\frac{C_0^*}2+\sum_{k=1}^\infty C_k^*\:T_k\left(x\right),
	  $$
	  (3,19)
	  取它的部分和
	- $$
	  C_n^*\left(x\right)=\frac{C_0}2+\sum_{k=1}^nC_k^*T_k\left(x\right),
	  $$
	  (3,20)
	  其误差为
	- $$
	  f(x)-C_n^*\left(x\right)\approx C_{n+1}^*T_{n+1}\left(x\right).
	  $$
	- 在[-1,1]上$T_{n+1}(x)$是均匀分布的，它的最大值$\max_{-1\leq x\leq1}|T_{n+1}(x)|$最小，因此$C_n^*(x)$可作为$f(x)$在[-1,1]上的近似最佳一致逼近多项式。