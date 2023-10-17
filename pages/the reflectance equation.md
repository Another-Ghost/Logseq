alias:: 反射方程

- To compute $L_o(\bold p, \bold v)$, we incorporate the [[BRDF]] into [[the reflectance equation]]:
  $$
  L_o(\mathbf{p},\mathbf{v})=\int_{\mathbf{l}\in\Omega^+}f(\mathbf{l},\mathbf{v})L_i(\mathbf{p},\mathbf{l})(\mathbf{n}\cdot\mathbf{l})\mathrm{d}\mathbf{l} \tag{2}
  $$
  or
  $$L_o(\bold{p}, \bold{\omega}_o) = \int_{\Omega ^ +} L_i(\bold{p}, \bold{\omega}_i) f(\bold{p}, \omega_i, \bold{\omega}_o) (\bold{n} \cdot \bold{\omega}_i)\,\mathrm{d}\bold{\omega} _i$$
  The $\bold l ∈\Omega^+$ subscript on the *integral sign* means that integration is performed over $\bold l$ vectors that lie in the [[unit hemisphere]] above the *surface* (centered on the [[surface normal]] $\bold n$) . 
  We use $\mathrm{d}\bold l$ to denote the [[differential]] [[solid angle]], 相当于是 $\mathrm{d}\omega_i$; $\mathrm{d}\bold v$ 相当于 $\mathrm{d}\omega_o$ .
- 之后的讨论是基于假设 **[[反射方程]]是[[position]]无关的**, we will omit the surface point $\bold p$ from $L_i()$,
  $L_o()$, and *the reflectance equation*:
  $$
  L_o(\mathbf{v})=\int_{\mathbf{l}\in\Omega}f(\mathbf{l},\mathbf{v})L_i(\mathbf{l})(\mathbf{n}\cdot\mathbf{l})d\mathbf{l} \tag{3}
  $$
- > In [[differential]] form:
  $$f(\bold l, \bold v)=\frac{\mathrm{d}L_o(\bold v)}{\mathrm{d}E_i(\bold l)}=\frac{\mathrm{d}{L_o(\bold v)}}{L_i(\bold l)\bold n\cdot\bold l\mathrm{d}\bold l}$$
- When computing *the reflectance equation*, the hemisphere is often parameterized
  using [[spherical coordinates]] $φ$ and $θ$. For this parameterization, the [[differential]] [[solid angle]] $\mathrm d\bold l$ is equal to $\sin θ_i \mathrm{d}θ_i \mathrm{d}φ_i$ ($\bold n\cdot\bold l=\theta_i$):
  $$
  L_o(\theta_o,\phi_o)=\int_{\phi_i=0}^{2\pi}\int_{\theta_i=0}^{\pi/2}f(\theta_i,\phi_i,\theta_o,\phi_o)L(\theta_i,\phi_i)\cos\theta_i\sin\theta_i\mathrm{d}\theta_i\mathrm{d}\phi_i \tag{4}
  $$
- In some cases it is convenient to use a slightly different parameterization, with the
  id:: 65093f0b-6235-4535-8762-c1ca419b7b62
  *cosines* of the [[elevation angles]] $µ_i = \cos θ_i$ and $µ_o = \cos θ_o$ as *variables* . For this parameterization, the *differential solid angle* $d\bold l$ is equal to $dµ_idφ_i$ .
  $$
  L_o(\mu_o,\phi_o)=\int_{\phi_i=0}^{2\pi}\int_{\mu_i=0}^{1}f(\mu_i,\phi_i,\mu_o,\phi_o)L(\mu_i,\phi_i)\mu_i\mathrm{d}\mu_i\mathrm{d}\phi_i \tag{5}
  $$
  The [[BRDF]] is defined only in cases where both the [light]([[light direction]]) and [[view directions]] are **above the [[surface]]**.
  >Evaluation of the BRDF for view directions under the surface can be avoided by clamping $n · v$ to $0$ or using its absolute value, but both approaches can result in artifacts. The Frostbite engine uses the absolute value of $n · v$ plus a small number ($0.00001$) to avoid divides by $0$ . Another possible approach is a “soft clamp,” which gradually goes to $0$ as the angle between $\bold n$ and $\bold v$ increases past $90^◦$.