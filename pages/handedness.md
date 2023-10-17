alias:: 偏手性

- # Definition
	- A [[right-handed basis]] is one for which $(\mathbf{V}_{1}\times\mathbf{V}_{2})\cdot\mathbf{V}_{3}>0$ .
	  logseq.order-list-type:: number
- ## 判别方法
  *拇指* 代表 $x$ 轴正向,
  *食指* 代表 $y$ 轴正向,
  *中指* 代表 $z$ 轴正向,
  符合左手就属于[[左手坐标系]]，符合右手就属于[[右手坐标系]]
-
- ## Reflection and Rotation
	- Performing an [[odd number]] of [[reflections]] **reverses** [[handedness]].
	- An [[even number]] of [[reflections]] is always equivalent to a [[rotation]].
	- So any series of *reflections* can always be regarded as **a single rotation** followed by **at most one reflection**.
	- The existence of a [[reflection]] within a $3\times3$ [[matrix]] can be detected by examining the [[determinant]]. If the determinant of a 3×3 matrix $\boldsymbol{M}$ is [[negative]], then **a reflection is present**. If the determinant is positive, then $\boldsymbol{M}$ preserves handedness.
	- ((64fa6ab4-4a9a-4a70-937b-50d1872373a2)) 
	  So when $\boldsymbol{M}$ is an [[orthogonal matrix]]:
	  If  $\operatorname{det}\boldsymbol{M} = 1$, the matrix $\boldsymbol{M} represents a **pure** [[rotation]]. 
	  If $\operatorname{det}\boldsymbol{M} =-1$, then the matrix $\boldsymbol{M}$ represents a [[rotation]] followed by a [[reflection]].
- [[OpenGL]]使用的是[[右手坐标系]] 
  [[Direct3D]]使用的是[[左手坐标系]]
  [[Unreal]]使用的是[[左手坐标系]]
-