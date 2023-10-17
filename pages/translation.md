alias:: 平移, translated, 平移变换

- ## Translation
	- A [[coordinate system]] is [[translated]] in space without otherwise affecting the *orientation* or *scale* of the axes by simply adding an *offset vector* . 
	  This operation **cannot** be expressed in terms of a $3\times 3$ *matrix* . 
	  Thus, To transform a point $\bold{P}$ from one coordinate system to another, we usually find ourselves performing the operation
	  $$
	  \bold{P}^{\prime}=\boldsymbol{M}\bold{P}+\bold{T}\tag{1}
	  $$
	  where $\boldsymbol{M}$ is some [[invertible]] $3\times 3$ *matrix* and $\bold{t}$ is a 3D [[translation vector]].
	- Performing two operations of the type shown in Equation $(1)$ results in the rather messy equation
	  id:: 64fd1571-4ee6-4a2b-9e7f-a61b9759d02b
	  $$
	  \begin{aligned}\bold{P}'&=\boldsymbol{M}_2\left(\boldsymbol{M}_1\bold{P}+\bold{T}_1\right)+\bold{T}_2\\&=\left(\boldsymbol{M}_2\boldsymbol{M}_1\right)\bold{P}+\boldsymbol{M}_2\bold{T}_1+\bold{T}_2\end{aligned} \tag{2}
	  $$
- ## Homogeneous Coordinates
	- Fortunately, there is a compact and elegant way to represent these transforms within a single mathematical entity.
	- We can do this by extending our vectors to *four-dimensional* [[homogeneous coordinates]] and using $4\times 4$ [[matrices]] to transform them. 
	  A *3D point* $\bold{P}$ is extended to *four dimensions* by setting its *fourth coordi-
	  nate*, which we call the [[w-coordinate]], equal to $1$. 
	  We construct a $4\times 4$ [[transformation matrix]] $\boldsymbol{F} corresponding to the $3\times 3$ *matrix* $\boldsymbol{M}$ and the *3D* [[translation]] $T$ as follows
	  $$\boldsymbol{F}=\left[\begin{array}{c}\boldsymbol{M}&\bold{T}\\ \bold{0}&1 \end{array}\right]
	  =\left[\begin{array}{c} M_{11}&M_{12}&M_{13}&T_x \\
	  M_{21}&M_{22}&M_{23}&T_y \\
	  M_{31}&M_{32}&M_{33}&T_z \\
	  0&0&0&1 \end{array}\right] \tag{3}$$
	  *Multiplying* this *matrix* by the *vector* $(P_{x},P_{y},P_{z},1)$ transforms the $x$, $y$, and $z$ *coordinates* of the vector in exactly the same way as Equation $(1) and leaves a $1$ in the $w$ *coordinate*. 
	  Furthermore, [[multiplying]] two transformation matrices of the form shown in Equation (1) yields another matrix of the same form that is equivalent to the pair of transforms performed in Equation (2).
- ## Inverse
	- If we solve Equation (1) for $\bold{P}$, we have
	  $$
	  \bold{P}=\boldsymbol{M}^{-1}\bold{P}^{\prime}-\boldsymbol{M}^{-1}\bold{T}
	  $$
	  We would therefore expect the [[inverse]] of the $4\times 4$ *matrix* $\bold{F}$ from Equation $(3)$ to be
	  $$\boldsymbol{F^{-1}}
	  =\left[\begin{array}{c}\boldsymbol{M^{-1}}&-\boldsymbol{M}^{-1}\bold{T}\\ \bold{0}&1 \end{array}\right]
	  =\left[\begin{array}{c} M_{11}^{-1}&M_{12}^{-1}&M_{13}^{-1}&-(\boldsymbol{M}^{-1}\bold{T})_x \\
	  M_{21}^{-1}&M_{22}^{-1}&M_{23}^{-1}&-(\boldsymbol{M}^{-1}\bold{T})_y \\
	  M_{31}^{-1}&M_{32}^{-1}&M_{33}^{-1}&-(\boldsymbol{M}^{-1}\bold{T})_z \\
	  0&0&0&1 \end{array}\right] \tag{4}$$
	  and the following computation verifies that this is true
	  $$\begin{aligned} \bold{FF}^{-1}
	  &=\left[\begin{array}{c}\boldsymbol{M}&\bold{T}\\ \bold{0}&1 \end{array}\right] \left[\begin{array}{c}\boldsymbol{M^{-1}}&-\boldsymbol{M}^{-1}\bold{T}\\ \bold{0}&1 \end{array}\right] \\
	  &=\left[\begin{array}{c}\boldsymbol{MM}^{-1}&\boldsymbol{M}(-\boldsymbol{M}^{-1}\bold{T})\bold{T}\\ \bold{0}&1 \end{array}\right] \\
	  &=\left[\begin{array}{c}\boldsymbol{I}_3&\bold{0}\\ \bold{0}&1 \end{array}\right] \\
	  &=\boldsymbol{I}_4
	  \end{aligned}
	  $$
- ## Points and Directions
	- To transform direction vectors using the same 4×4 transformation matrices that we use to transform points, we extend direction vectors to four dimensions by setting the w coordinate to 0. This nullifies the fourth column of the matrix F in Equation(4.25), leaving only the upper left 3×3 portion of the matrix to affect the direction vector
-