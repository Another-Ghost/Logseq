alias:: directional albedo

- The [[directional-hemispherical reflectance]] $R(\bold l)$ is a function related to the [[BRDF]] and [[the reflectance equation]] . It can be used to **measure to what degree a BRDF is [[energy conserving]]**.
  It measures the amount of light coming from a given direction that is [[reflected]] **at all**, into any outgoing direction in the *hemisphere* around the surface normal. 
  Essentially, it measures [[energy loss]] for a given [[incoming direction]]:
  $$
  R(\mathbf{l})=\int_{\mathbf{v}\in\Omega}f(\mathbf{l},\mathbf{v})(\mathbf{n}\cdot\mathbf{v})d\mathbf{v} \tag{7}
  $$
- A similar but in some sense **opposite** function, [[hemispherical-directional reflectance]] $R(\bold v)$ can be similarly defined:
  $$
  R(\mathbf{v})=\int_{\mathbf{l}\in\Omega}f(\mathbf{l},\mathbf{v})(\mathbf{n}\cdot\mathbf{l})d\mathbf{l} \tag{8}
  $$
  or
  $$
  R(\bold{\omega}_o)=\int_{\Omega^{+}}f(\mathbf{\omega}_i,\mathbf{\omega}_o)\cos\theta_i\mathrm{d}\mathbf{\omega}_i
  $$
- If the BRDF is [reciprocal]([[Helmholtz reciprocity]]), then the [[hemispherical-directional reflectance]] and the [[directional-hemispherical reflectance]] are **equal** and the same function can be used to compute either one. 
  [[directional albedo]] can be used as a blanket term for both reflectances in cases where they are used interchangeably.
- The value of the [[directional-hemispherical reflectance]] $R(\bold l)$ must always be in the *range* $[0, 1]$, as a result of [[energy conservation]]. 
  A reflectance value of $0$ represents a case where all the incoming light is [[absorbed]] or otherwise lost. 
  If all the light is [[reflected]], the reflectance will be 1. 
  In most cases it will be somewhere between these two values.
- Like the BRDF, the values of $R(\bold l)$ vary with [[wavelength]], so it is represented as an [[RGB vector]] for rendering purposes. Since each component (red, green, and blue) is restricted to the range $[0, 1]$, a value of $R(\bold l)$ can be thought of as a [[simple color]]. 
  >Note that this restriction does not apply to the values of the BRDF. As a [[distribution function]], the BRDF can have [[arbitrarily]] high values in certain directions (such as the center of a [[highlight]]) if the distribution it describes is highly [[nonuniform]].
- The requirement for a BRDF to be [[energy conserving]] is that $R(l)$ be no greater than $1$ for **all possible values** of $\bold l$ .