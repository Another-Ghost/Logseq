- [[Split Sum Approximation]]是对于[[the rendering equation]]的近似：
  \begin{equation}
  L_o(p, \omega_o) \approx \frac{\int_{\Omega_{f_r}} L_i(p, \omega_i)\,\mathrm{d}\omega_i}{\int_{\Omega_{f_r}} (p, \omega_i)\,\mathrm{d}\omega_i}
  \cdot \int_{\Omega^+} f_r(p, \omega_i, \omega _o)\cos\theta_i\,\mathrm{d}\omega_i
  \end{equation}
- 第一部分 可[[预计算]]一个[[环境光]]的[[prefilter map]]。
- 第二不分 可