alias:: screen mapping stage

- #RenderingPipelineStage
- ### Screen Coordinates
	- Only the [[clipped]] [[primitives]] are passed on to the [[screen mapping stage]], and the *coordinates* are still *three-dimensional* when entering this stage.
	  The *x-coordinates* and *y-coordinates* of each primitive are *transformed* to form [[screen coordinates]].
- ### Window Coordinates
	- [[Screen coordinates]] together with the *z-coordinates* are also called [[window coordinates]].
- ### Screen Coordinates to Window Coordinates
	- Assume that the scene should be rendered into a window with the *minimum* [[corner]] at $(x_1, y_1)$ and the *maximum* [[corner]] at $(x_2, y_2)$, where $x1 < x2$ and $y1 < y2$. Then the [[screen mapping]] is a [[translation]] followed by a [[scaling]] operation. The new *x-coordinates* and *y-coordinates* are said to be [[screen coordinates]].
	- The *z-coordinate* ($[−1, +1]$ for [[OpenGL]] and $[0, 1]$ for [[DirectX]]) is also mapped to $[z_1, z_2]$, with $z_1 = 0$ and $z_2 = 1$ as the default values. 
	  These can be changed with the *API*, however.
	- The [[window coordinates]] along with this remapped *z-value* are passed on to the [[rasterizer stage]].
- ### How Integer and Floating Point Values relate to Pixels 
  Given a [[horizontal array]] of *pixels* and using [[Cartesian coordinates]], 
  the *left edge* of the *leftmost pixel* is $0.0$ in *floating point coordinates*.  
  The [[center]] of this *pixel* is at $0.5$. So, a *range of pixels* $[0, 9]$ cover a span from $[0.0, 10.0)$. The conversions are simply
  $$d=\operatorname{floor}(c)$$
  $$c = d+0.5$$
  where $d$ is the *discrete integer index* of the *pixel* 
  and $c$ is the *continuous floating point value* within the *pixel*.
- ### Window Coordinates in OpenGL and DirectX
  While **all** *APIs* have *pixel location values* that increase going **from left to right**. 
  OpenGL favors the Cartesian system throughout, treating the *lower left corner* as the *lowest-valued element* $(0,0)$, 
  while DirectX sometimes defines the **upper left corner** as this *element*, depending on the context.