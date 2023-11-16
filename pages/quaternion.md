alias:: 四元数

- # Reference
	- ![quaternion.pdf](../assets/quaternion_1700088327636_0.pdf)
- # Definition
	- 四元数形如
	  logseq.order-list-type:: number
	  id:: 64fe6843-78b3-416f-94e6-12efb022c886
	  $$\bold{q}=(\bold v, w)=x\bold{i}+y\bold{j}+z\bold{k}+w= \bold {v}+w$$
	  $$\bold v=(x,y,z)=x\bold{i}+y\bold{j}+z\bold{k}$$
	  其中 $x,y, z,w$ 都是[[实数]], $\bold i, \bold j, \bold k$ 满足
	  $$\bold{i}^2=\bold{j}^2=\bold{k}^2=-1$$
	  $$\bold{ij=-ji=k,\quad jk=-kj=i,\quad ki=-ik=j}$$
	  $w$ 称为[[四元数]] $\bold q$ 的[[虚部]], $\bold v$ 称为 $\bold{q}$ 的[[实部]]。
	  > 对于[[虚部]] $\bold v$, 我们可以对其进行所有[[向量运算]].
	- [[四元数]]是[[复数]]的[[不可交换]]的延伸。
	  logseq.order-list-type:: number
	- 易证所有[[四元数]]组成的[[集合]] $\bold H$ 称为成为一个有[[单位元]]的[[非交换环]], 也成为一个[[除环]], 称为[[四元数环]].
	  logseq.order-list-type:: number
	- # 四元数运算
	  设$\bold q,\bold q_1,\bold q_2$ 都是[[四元数]]。
		- ### [[乘法]]
		  logseq.order-list-type:: number
		  $$\bold q_1\bold q_2=(\bold v_1\times\bold v_2+w_2\bold v+w_1\bold v_2, w_1 w_1-\bold v_1\cdot\bold v_2)$$
		  ([[向量点乘]], [[向量叉乘]])
		  注意乘法不具有[[交换律]].
		- ### [[加法]]
		  logseq.order-list-type:: number
		  id:: 64ffa4ed-4dd1-469a-b9b1-2ba8db9240bb
		  $$\bold q_1+\bold r_2=(\bold v_1 +\bold v_2, w_1+w_2)$$
		- ### [[共轭]]
		  logseq.order-list-type:: number
		  $$\bar{\bold q}=(-\bold v, w)$$
		- [[norm]]
		  logseq.order-list-type:: number
		  \begin{aligned}
		  \Vert\bold q\Vert=n(\bold q)&=\sqrt{\bold q\bar{\bold q}}=\sqrt{\bold{v}\cdot\bold {v}+w^2} \\
		  &=\sqrt{x^2+y^2+z^2+w^2}
		  \end{aligned}
		- [[单位元]]
		  logseq.order-list-type:: number
		  $$\bold i=(\bold 0, 1)$$
		- [[逆]]
		  logseq.order-list-type:: number
		  $$\Vert\bold q\Vert=\bold q\bar{\bold q}\Longleftrightarrow \frac{\bold q\bar{\bold q}}{\Vert\bold q\Vert}=1$$
		  $$\bold q^{-1}=\frac{1}{\Vert\bold q\Vert}\bar{\bold q}$$
		- [[数量乘法]]
		  logseq.order-list-type:: number
		  $$s\bold q=(\bold{0},s)(\bold v, w)=(s\bold v, sw)=(\bold v, w)(\bold 0, s)=(\bold v, w)(\bold 0, s)$$
		  所以数量乘法是有[[交换律]]的。
- # 四元数旋转 #DOING
	- The [[unit]] [[quaternion]] $q$ corresponding to a [[rotation]] through the [[angle]] $θ$ about the [[axis]] $\bold A$ is given by
	  $$\bold q=\cos\frac{\theta}{2}+\bold A\sin\frac{\theta}{2}$$
	- $\bold q$ 对应的[[旋转矩阵]]为：
	  $$
	  \boldsymbol R_\bold{q}=\begin{bmatrix}1-2y^2-2z^2&2xy-2wz&2xz+2wy\\2xy+2wz&1-2x^2-2z^2&2yz-2wx\\2xz-2wy&2yz+2wx&1-2x^2-2y^2\end{bmatrix}
	  $$
	  $$\bold{qPq}^{-1}=\boldsymbol R{\bold P}$$
	-
-