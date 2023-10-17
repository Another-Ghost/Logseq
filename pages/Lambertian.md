alias:: Lambertian shading model, Lambertian shading, Lambertian reflection, Lambert

- # Definition
	- An **idealized** [[diffuse surface]] is called [[Lambertian]].
	  logseq.order-list-type:: number
- [[Lambert's law]]
- The **simplest** possible [[BRDF]] is [[Lambertian]], which corresponds to the [[Lambertian shading model]].
- The [[Lambertian BRDF]] has the $(n · l)$ *factor* that distinguishes Lambertian shading is **not part of the BRDF** but rather **part of [[the reflectance equation]]** .
  id:: 6509586d-3a63-4cff-b853-0143834f743a
- The [[Lambertian BRDF]] is often used in [[real-time rendering]] to represent [[local subsurface scattering]] (though it is being **supplanted by more accurate models** #TODO ).
- The [[directional-hemispherical reflectance]] of a [[Lambertian]] surface is also a *constant*:
  id:: 650a4d13-5120-471d-9cbb-178e5af327dd
  \begin{aligned}
  R(\bold{\omega}_o) &=\int_{\Omega^{+}}f_{Lambert}(\mathbf{\omega}_i,\mathbf{\omega}_o)\bold n\cdot \omega_i\mathrm{d}\mathbf{\omega}_i \\
  &=\int_{\phi_i=0}^{2\pi}\int_{\theta_i=0}^{\pi/2}f_{Lambert}\cos\theta_i\sin\theta_i\mathrm{d}\theta_i\mathrm{d}\phi_i \\
  &= \pi f_{Lambert} \\
  &=\bold c_{diff}=\rho=\rho_{ss} \tag{9}
  \end{aligned}
  其中 $f_{Lambert}$ 是常数。
- The *constant [[reflectance value]]* of a [[Lambertian BRDF]] is typically referred to as the [[diffuse color]] $\bold c_{diff}$ or the [[albedo]] $ρ$. 
  id:: 650a4d13-161b-4ae7-953a-04d9f88769f2
  To emphasize the connection with [[subsurface scattering]], we will refer to this quantity as the [[subsurface albedo]] $ρ_{ss}$ . The BRDF from $(9)$ gives the following result:
  $$f_{Lambert}=\frac{\rho_{ss}}{\pi}$$
  > The $1/π$ factor is caused by the fact that *integrating* a [[cosine]] factor over the [[hemisphere]] yields a value of $π$. Such factors are often seen in BRDFs.