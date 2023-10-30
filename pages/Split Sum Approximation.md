- [[Split Sum Approximation]]是对于[[the rendering equation]]的近似：
  \begin{equation}
  L_o(p, \omega_o) \approx \frac{\int_{\Omega_{f_r}} L_i(p, \omega_i)\,\mathrm{d}\omega_i}{\int_{\Omega_{f_r}} (p, \omega_i)\,\mathrm{d}\omega_i}
  \cdot \int_{\Omega^+} f_r(p, \omega_i, \omega _o)\cos\theta_i\,\mathrm{d}\omega_i
  \end{equation}
- 第一部分为 光照 对[[lobe]]范围的 积分 然后除以 lobe的大小 来取 平均值， 可通过[[预计算]]一个[[环境光]]的[[prefilter map]]。
- 第二不分 可结合 [[Schlick's approximation]]：
  \begin{aligned}
  \int_{\Omega^+}f_r \cos\theta_i \,\mathrm{d}\omega_i &\approx \int_{\Omega^+} \frac{f_r}{F}(1 - (1 - \cos\theta )^5) \cos\theta_i \,\mathrm{d}\omega_i \\
  &+\int_{\Omega^+}\frac{f_r}{F}(1 - \cos\theta )^5 \cos\theta_i \,\mathrm{d}\omega_i
  \end{aligned}
  两个部分都可以[[预计算]]
-