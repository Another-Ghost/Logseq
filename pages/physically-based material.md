- 对于使用主流[[BRDF model]]的材质，其表面[[反射方程]]为：
- \begin{aligned}
  L_o(p,\omega_o)&=\int_{\Omega^+}(k_df_{Lambert}+k_sf_{Torrance})L_i(p,\omega_i)(n\cdot\omega_i)\,\mathrm{d}\omega_i \\
  &=\int_{\Omega^+}(k_df_{Lambert}+k_sf_{Torrance})L_i(p,\omega_i)(n\cdot\omega_i)\,\mathrm{d}\omega_i+\int_{\Omega^+}(k_df_{Lambert}+k_sf_{Torrance})L_i(p,\omega_i)(n\cdot\omega_i)\,\mathrm{d}\omega_i
  \end{aligned}
-