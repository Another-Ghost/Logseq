- alias::局部光照
- # Definition
	- [[局部光照]]模型采用[[反射方程]]在每个[[表面点]]处局部地计算[[着色]]。
	  logseq.order-list-type:: number
	  在局部光照算法中，$L_i(\bold l)$ 已经是**预先给定**的.
- 接下来的我们把 $L_{i}(\bold l)$ 限制在[[定向光源]]和[[点光源]].
- 我们考虑一个小而远的[[面光源]]，并将 $\bold l_c$ 定义为由表面点指向其中心。我们还将光的[[颜色]] $c_{light}$ 定义为 *[[白色]][[Lambertian]]表面* 朝向 *面光源中心*（$\bold n =\bold l_c$） *反射* 的[[radiance]]。
- 我们把一个[[定向光源]]或[[点光源]]视为将[[面光源]]的大小缩小到 $0$ 的 *极限* 情况，同时保持 $\bold c_{light}$ 不变。
  在这种情况下，[[反射方程]]中的积分简化为对单个[[BRDF]]求值：
  $$L_o(\bold v)=\pi f(\bold l_c, \bold v)\bold c_{light}(\bold n\cdot \bold l_c)$$
  $(\bold n\cdot \bold l)$ 通常被限制最小为 $0$，用来跳过 *表面下方光源* :
  $$L_o(\bold v)=\pi f(\bold l_c, \bold v)\bold c_{light}(\bold n\cdot \bold l_c)^+$$
  当有多个[[光源]]时：
  $$L_o(\bold v)=\pi\sum_{i=1}^n f(\bold l_{c_i}, \bold v)\bold c_{light_i}(\bold n\cdot \bold l_{c_i})^+$$
-