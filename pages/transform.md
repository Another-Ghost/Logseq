alias:: transformed, transforms, transformation

- # 原理
  现有一个[[父坐标空间]] $\boldsymbol P$ 和一个 [[子坐标空间]] $\boldsymbol C$。
  设$\boldsymbol M_{c\to p}$ 表示把[[子坐标空间]]的[[点]]或[[方向矢量]] $\bold a_c$ 变换到[[父坐标空间]]下的点或方向矢量 $\bold a_p$ ;
  设$\boldsymbol M_{p\to c}$ 表示把[[父坐标空间]]的[[点]]或[[方向矢量]] $\bold a_p$ 变换到[[子坐标空间]]下的点或方向矢量 $\bold a_c$ :
  $$\bold a_p=\boldsymbol M_{c\to p}\bold a_c$$
  $$\bold a_c=\boldsymbol M_{p\to c}\bold a_p$$
  由定义可得 $\boldsymbol M_{c\to p}$ 与 $\boldsymbol M_p\to c$ 互为[[逆矩阵]]:
  $$\boldsymbol M_{p\to c} = \boldsymbol M_{c\to p}^{-1}$$
- [[子坐标空间]] $\boldsymbol{C}$ 的 $3$ 个[[坐标轴]]在[[父坐标空间]] $\boldsymbol {P}$ 下的 *方向* [[坐标]]为 $\bold x_{c}, \bold y_c, \bold z_c$, 以及其原点 *位置* [[坐标]] $\bold o_c$ 。 
  $$\boldsymbol M_{c\to p}=\left[\begin{aligned}\begin{array}{c}
  \vert&\vert&\vert&\vert \\
  \bold x_c&\bold y_c&\bold z_c&\bold o_c \\
  \vert&\vert&\vert&\vert \\
  0&0&0&1
   \end{array}\end{aligned}\right]$$
  $\vert$ 表示[[按列展开]]。($-$ 表示[[按行展开]])
- 因为不需要[[平移变换]]，所以对[[方向矢量]]的坐标变换可以使用 $3\times 3$ 的 *矩阵* 来表示。此时的 *变换矩阵* 为
  $$\boldsymbol M_{c\to p}=\left[\begin{aligned}\begin{array}{c}
  \vert&\vert&\vert \\
  \bold x_c&\bold y_c&\bold z_c \\
  \vert&\vert&\vert
   \end{array}\end{aligned}\right]$$
  如果 $\boldsymbol M_{c\to p}$ 为[[正交矩阵]]，已知 [[父坐标空间]] $\boldsymbol{P}$ 的 $3$ 个[[坐标轴]]在[[子坐标空间]] $\boldsymbol {P}$ 下的 *方向* [[坐标]]为 $\bold x_{p}, \bold y_p, \bold z_p$, 则
- $$\boldsymbol M_{p\to c}
  =\left[\begin{aligned}\begin{array}{c}
  \vert&\vert&\vert \\
  \bold x_p&\bold y_p&\bold z_p \\
  \vert&\vert&\vert
   \end{array}\end{aligned}\right]
  =\boldsymbol M_{c\rightarrow p}^{-1}=\boldsymbol M_{c\rightarrow p}^{T}\\
  =\left[\begin{aligned}
  -\quad&\bold x_c&- \\
  -\quad&\bold y_c&- \\
  -\quad&\bold y_c&- \\
  \end{aligned}\right]
  $$
- 则
  $$M_{c\to p}=\left[\begin{aligned}\begin{array}{c}
  \vert&\vert&\vert \\
  \bold x_c&\bold y_c&\bold z_c \\
  \vert&\vert&\vert
   \end{array}\end{aligned}\right]
  =\left[\begin{aligned}
  -\quad&\bold x_p&- \\
  -\quad&\bold y_p&- \\
  -\quad&\bold y_p&- \\
  \end{aligned}\right]$$
  则完成的[[齐次坐标]]下的 $\bold M_{p\to c}$ 也可以表示为
  $$\boldsymbol M_{c\to p}
  =\left[\begin{aligned}\begin{array}{c}
  \vert&\vert&\vert&\vert \\
  \bold x_c&\bold y_c&\bold z_c&\bold o_c \\
  \vert&\vert&\vert&\vert \\
  0&0&0&1
   \end{array}\end{aligned}\right]
  =\left[\begin{aligned}\begin{array}{c}
  - &\bold x_p&-&\vert \\
  - &\bold y_p&-&\bold o_c \\
  - &\bold z_p&-&\vert \\
  0&0&0&1
   \end{array}\end{aligned}\right]$$
- ## 验证方法
	- 例如已知[[坐标空间]] $\boldsymbol B$ 的 $x$ *轴* ，$y$ *轴* ，$z$ *轴* 在 *坐标空间* $\boldsymbol A$ 下的表示为 $\bold x_B, \bold y_B, \bold z_B$。设从 $\boldsymbol A$ 到 $\boldsymbol B$ 的[[变换矩阵]]为 $\boldsymbol M_{A\to B}$， 则
	  $$\boldsymbol M_{A\to B}\bold x_{B}=(1,0,0)$$
	  所以当不知道这些[[坐标向量]]应该[[按行展开]]还是[[按列展开]]排放 *变换矩阵* 中时，可以用这个等式来验证。
-
- # 常用变换
- |Notation|Name|Characteristics|[[affine]]|[[linear]]|
  |--|--|--|--|--|
  |$\boldsymbol T(\bold t)$|[[translation matrix]]|Moves a point by vector $\bold t$. |Y|N|
  |$\boldsymbol R_x(\rho)$|[[rotation matrix]]|Rotates $ρ$ radians around the $x$-axis.|Y|Y|
  |$\boldsymbol R$|[[rotation matrix]]|Any rotation.|Y|Y|
  |$\boldsymbol S(\bold s)$|[[scaling matrix]]|Scales along all $x, y, z$ axes according to $s$|Y|Y|
  |$\boldsymbol H_{ij}(s)$|[[shear matrix]]|Shears [[component]] $i$ by a factor $s$, [:br]with respect to component $j$, $i,j\in{x,y,z}$|Y|Y|
  |$\boldsymbol E(y, p, r)$|[[Euler transform]]|[[orientation matrix]] given by the [[Euler angles]] [[yaw]],[[pitch]],[[roll]]|Y|Y|
  |$\boldsymbol P_0(s)$|[[orthographic projection]]|[[Parallel projects onto some plane or to a [[volume]]|Y|Y|
  |$\boldsymbol P_p(s)$|[[perspective projection]]|[[Projects]] with [[perspective]] onto a plane or to a volume|N|N|
  |$\operatorname{slerp}(\bold q_1, \bold q_2, t)$|[[slerp transform]]|Creates an [[interpolated quaternion]] with respected to the quaternions $\bold q_1$ and $\bold q_2$, and the parameter $t$ |Y|Y|
-