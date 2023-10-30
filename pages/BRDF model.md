alias:: BRDF models

- 主流模型中[[Specular BRDF]]采用[[Cook-Torrance BRDF]]，[[Diffuse BRDF]]采用 [[Lambertian BRDF]]：
- \begin{aligned}
  f&=k_df_{Lambert}+k_sf_{Torrance} \\
  &=k_d\frac{\bold c_{diff}}{\pi}+k_s\frac{F(\bold \omega_i, \bold h)G(\omega_i,\omega_o,\bold h)D(\bold h)}{4(\bold n,\bold\omega_i)(\bold n, \bold\omega_o)}
  \end{aligned}