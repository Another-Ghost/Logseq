alias:: 偏导数, partial derivatives, partial differentiation, partial differentiations

- [[函数]]$\bold f$ 把 [[开集]]$E{\subset}\mathbb{R}^n$ 映入 $\mathbb{R}^n$ . 设 $\{\boldsymbol e_1,\cdots, \boldsymbol e_n)\}$ 及 $\{\boldsymbol u_1,\cdots, \boldsymbol u_m)\}$分别是 $R^n$ 及 $R^m$ 的[[标准基]]。$\bold f$ 的[[分量]]是由
  id:: 655f636b-c852-4805-8828-90be940f31ff
  $$
  \bold f(\boldsymbol x)=\sum_{i=1}^{m}f_{i}(\boldsymbol x)\boldsymbol u,\quad(\boldsymbol x\in E),
  $$
  确定的[[实函数]] $f_1,\cdots,f_{m}$； 
  上式还可以等价地写成
  $$
  f_{i}(\boldsymbol x)=\mathbf{f}(\boldsymbol x)\cdot\boldsymbol{u}_{i},\quad 1\le i\le m.$$
- 对于 $\boldsymbol x\in E$, $1\le i\le m$, $1\le j\le n$ 定义
  id:: 655f66cc-bfc6-4ef8-a450-eb25f2146c8d
- id:: 655f66cc-ac6c-4bf4-90a8-ab4bb4278dc7
  $$
  (D_j f_i)(x)=\lim_{t\to0}\frac{f_{i}(x+te_{i})-f_{i}(x)}t.
  $$
  这里截定此极限存在。把$f_i(x)$写成$f_i(x_1,...,x_i)$,就知道$D_if_i$是$f_i$对于$x_j$
- 的导数(其他变量保持不变)。所以，经常用记号
  $\frac{\partial f_i}{\partial x_i}$
  代替$D,f_i$,而$D_if_i$被叫做偏导数。
-