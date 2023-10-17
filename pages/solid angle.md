alias:: 立体角

- # Definition
	- 以 *观测点* 为[[球心]], 构造一个[[单位球面]]，任意 *对象* [[投影]]到该 *单位球面* 上的 *投影* [[面积]]，即为该 *对象* 相对于该 *观测点* 的[[立体角]] . 
	  logseq.order-list-type:: number
	  因此，[[立体角]]是 *单位球面* 上的一块[[面积]]。
	- Similar to [[angle]], a [[solid angle]] measures the size of a [[continuous set]] of [[directions]] in *three-dimensional space*, measured in [[steradians]], 单位是 $\mathrm{sr}$. which are defined by the [[area]] of the intersection patch on an enclosing [[sphere]] with [[radius]] 1. 
	  logseq.order-list-type:: number
	- A solid angle in steradians is the ratio of the area covered on a sphere by to the square of the radius of said sphere.
	  logseq.order-list-type:: number
	  [[Solid angle]] is represented by the symbol $ω$
	  $$\omega=\frac{A}{r^2}$$
	  其中 $A$ 代表 *面积*，$r$ 为 *半径*。
	- ## 立体角的微分
	  logseq.order-list-type:: number
	  在[[球坐标系]]中:
	  $$
	  \mathrm{d}A=(r\sin\theta\mathrm{d}\varphi)(r\mathrm{d}\theta)=r^2(\sin\theta\mathrm{d}\theta\mathrm{d}\varphi)
	  $$
	  $$
	  \mathrm{d}\omega=\frac{\mathrm{d}A}{r^2}=\sin\theta\mathrm{d}\theta\mathrm{d}\varphi 
	  $$
	- ## 封闭曲面立体角
	  logseq.order-list-type:: number
	  一个完整的[[球面]]对于球内任意一点的[[立体角]]为 $4\pi\ \mathrm{sr}$
	  $$
	  \oiint_S\sin\theta\mathrm{d}\theta\mathrm{d}\varphi=\int_0^\pi\sin\theta \mathrm{d}\theta\int_0^{2\pi}\mathrm{d}\varphi=[-\cos\theta]_0^\pi(2\pi)=4\pi 
	  $$