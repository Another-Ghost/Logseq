alias:: 偏导数, partial derivatives, partial differentiation, partial differentiations

- [[函数]]$\bold f$ 把 [[开集]]$E{\subset}\mathbb{R}^n$ 映入 $\mathbb{R}^n$ . 设 $\{\boldsymbol e_1,\cdots, \boldsymbol e_n)\}$ 及 $\{\boldsymbol u_1,\cdots, \boldsymbol u_m)\}$分别是 $R^n$ 及 $R^m$ 的[[标准基]]。$\bold f$ 的[[分量]]是由
  id:: 655f636b-c852-4805-8828-90be940f31ff
  $$
  \bold f(\boldsymbol x)=\sum_{i=1}^{m}f_{i}(\boldsymbol x)\boldsymbol u,\quad(\boldsymbol x\in E),
  $$
  确定的[[实函数]] $f_1,.,f_{m}$ (24)式还可以等价地写成
- $$
  f_{i}(x)=\mathbf{f}(x)\cdot\mathbf{u}_{i}\:,\quad1\:s_{i}\:i\:s_{i}\:m.
  $$
- 材干$x\in E$,1后$i\xi_{0}m,1\xi_{0}j\xi_{0}n$,定义
- $$
  (D,f,)(x)=\lim_{i\to0}\frac{f_{i}(x+te_{i})-f_{i}(x)}t.
  $$
  这里截定此极限存在。把$f_i(x)$写成$f_i(x_1,...,x_i)$,就知道$D_if_i$是$f_i$对于$x_j$
- 的导数(其他变量保持不变)。所以，经常用记号
  $\frac{\partial f_i}{\partial x_i}$
  代替$D,f_i$,而$D_if_i$被叫做偏导数。
-