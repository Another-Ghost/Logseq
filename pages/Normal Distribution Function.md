alias:: NDF, 法线分布函数

- ## [[Beckmann NDF]]
	- 类似于[[正太分布/密度函数]]，但是定义在[[slope space]]：
	  $$D(h) = \frac{e^{-\frac{\tan^2\theta_h}{\alpha^2}}}{\pi\alpha^2\cos^4\theta_h}$$
	  $\alpha$ ：表面 的[[roughness]]（越小越接近[[镜面反射]]）
	  $\theta_h$ ： [[half vector]] $h$ 和 [[normal]] $n$ 之间的夹角。
		- $D(h)$ 在[[projected solid angle]]上积分为 $1$ 。
- [[GGX]]
-