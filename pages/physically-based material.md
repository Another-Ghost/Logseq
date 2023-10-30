- 对于使用主流[[BRDF model]]的材质，其表面[[反射方程]]为：
- \begin{aligned}
  L_o(p,\omega_o)&=\int_{\Omega^+}(k_df_{Lambert}+k_sf_{Torrance})L_i(p,\omega_i)(n\cdot\omega_i)\,\mathrm{d}\omega_i \\
  &=\int_{\Omega^+}k_d\frac{\bold c_{diff}}{\pi}L_i(p,\omega_i)(n\cdot\omega_i)\,\mathrm{d}\omega_i+\int_{\Omega^+}k_s\frac{F(\bold \omega_i, \bold h)G(\omega_i,\omega_o,\bold h)D(\bold h)}{4(\bold n,\bold\omega_i)(\bold n, \bold\omega_o)}L_i(p,\omega_i)(n\cdot\omega_i)\,\mathrm{d}\omega_i
  \end{aligned}
- 其中第一部分相当于[[diffuse reflection]]，可以[[预计算]]一个[[irradiance map]]存储任一方向的对 [[Lambertian BRDF]] 进行 半球范围的光照积分 后求得的 反射值（是个常数）；
  第二部分相当于 [[specular reflection]]，可以应用 [[Split Sum Approximation]]。
-