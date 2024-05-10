alias:: z-transform table

- id:: 65fc975b-c805-436c-b870-2dbff8925c74
  | # | Sequence | Z-transform | ROC |
  | 1 | $δ(n)$     | $1$           | Entire z-plane except $z = 0$ |
  | 2 | $u(n)$     | $\frac{z}{z-1}=\frac{1}{1-z^{-1}}$ | $\vert z\vert > 1$ |
  | 3 | $u(-n - 1)$ | $-\frac{z}{z-1}=\frac{-1}{1-z^{-1}}$ | $\vert z\vert < 1$ |
  | 4 | $a^n u(n)$ | $\frac{z}{z-a}=\frac{1}{1-a z^{-1}}$ | $\vert z\vert > \vert a\vert$ |
  | 5 | $a^n u(-n - 1)$ | $\frac{-z}{z-a}=\frac{-1}{1-a z^{-1}}$ | $\vert z\vert  < \vert a\vert$  |
  | 6  | $R_N(n)$   | $\frac{z^{N}-1}{z^{N-1}(z-1)}=\frac{1-z^{-N}}{1-z^{-1}}$ | $\vert z\vert  > 0$ |
  | 7  | $n u(n)$   | $\frac{z}{(z-1)^{2}}=\frac{z^{-1}}{\left(1-z^{-1}\right)^{2}}$ | $\vert z\vert  > 1$ |
  | 8  | $n a^n u(n)$ | $\frac{a z}{(z-a)^{2}}=\frac{a z^{-1}}{\left(1-a z^{-1}\right)^{2}}$ | $\frac{a z}{(z-a)^{2}}=\frac{a z^{-1}}{\left(1-a z^{-1}\right)^{2}}$  |
  | 9  | $n a^n u(-n - 1)$ | $\frac{-a z}{(z-a)^{2}}=\frac{-a z^{-1}}{\left(1-a z^{-1}\right)^{2}}$ | $\vert z\vert  < \vert a\vert$  |
  | 10 | $e^{-\alpha n} u(n)$ | $\frac{z}{z-\mathrm{e}^{-\mathrm{j} \omega_{0}}}=\frac{1}{1-\mathrm{e}^{-\mathrm{j} \omega_{0}} z^{-1}}$ | $\vert z\vert  > 1$ |
  | 11 | $\sin(\omega_0 n) u(n)$ | $\frac{z \sin \omega_{0}}{z^{2}-2 z \cos \omega_{0}+1}=\frac{z^{-1} \sin \omega_{0}}{1-2 z^{-1} \cos \omega_{0}+z^{-2}}$ | $\vert z\vert  > 1$ |
  | 12 | $\cos(\omega_0 n) u(n)$ | $\frac{1 - z^{-1} e^{-\alpha} \cos \omega_0}{1 - 2z^{-1} e^{-\alpha} \cos \omega_0 + z^{-2} e^{-2\alpha}}$ | $\vert z\vert  > 1$ |
  | 13 | $e^{-\alpha n} \sin(\omega_0 n) u(n)$ | $\frac{z^{-1} \mathrm{e}^{-a} \sin \omega_{0}}{1-2 z^{-1} \mathrm{e}^{-a} \cos \omega_{0}+z^{-2} \mathrm{e}^{-2 a}}$ | $\vert z\vert  > e^{-\alpha}$ |
  | 14 | $e^{-\alpha n} \cos(\omega_0 n) u(n)$ | $\frac{1-z^{-1} \mathrm{e}^{-a} \cos \omega_{0}}{1-2 z^{-1} \mathrm{e}^{-a} \cos \omega_{0}+z^{-2} \mathrm{e}^{-2 a}}$ | $\vert z\vert  > e^{-\alpha}$ |
  | 15 | $\sin \left(\omega_{0} n+\theta\right) u(n)$  | $\frac{z^{2} \sin \theta+z \sin \left(\omega_{0}-\theta\right)}{z^{2}-2 z \cos \omega_{0}+1}=\frac{\sin \theta+z^{-1} \sin \left(\omega_{0}-\theta\right)}{1-2 z^{-1} \cos \omega_{0}+z^{-2}}$  | $\vert z\vert>1$ |
  | 16 | $\cos \left(\omega_{0} n+\theta\right) u(n)$ | $\frac{z^{2} \sin \theta+z \sin \left(\omega_{0}-\theta\right)}{z^{2}-2 z \cos \omega_{0}+1}=\frac{\sin \theta+z^{-1} \sin \left(\omega_{0}-\theta\right)}{1-2 z^{-1} \cos \omega_{0}+z^{-2}}$| $\vert z\vert>1$ |
  | 17 | $(n+1)a^n u(n)$ | $\frac{z^{2}}{(z-a)^{2}}=\frac{1}{\left(1-a z^{-1}\right)^{2}}$ | $\vert z\vert  > \vert a\vert$ |
  | 18 | $\frac{(n+1)(n+2)}{2!} a^n u(n)$ | $\frac{z^{3}}{(z-a)^{3}}=\frac{1}{\left(1-a z^{-1}\right)^{3}}$ | $\vert z\vert  > \vert a\vert$ |
  | 19 | $\frac{(n+1)(n+2)...(n+m)}{m!} a^n u(n)$ | $\frac{z^{m+1}}{(z-a)^{m+1}}=\frac{1}{\left(1-a z^{-1}\right)^{m+1}}$ | $\vert z\vert  > \vert a\vert$  |
  | 20 | $n a^{n-1} u(n)$ | $\frac{z}{(z-a)^{m+1}}=\frac{z^{-m}}{\left(1-a z^{-1}\right)^{m+1}}$ | $\vert z\vert  > \vert a\vert$ |
  | 21 | $$\frac{n(n-1) \cdots(n-m+1)}{m !} a^{n-m} u(n)$$  | $$\frac{z}{(z-a)^{m+1}}=\frac{z^{-m}}{\left(1-a z^{-1}\right)^{m+1}}$$  | $\vert z\vert  > \vert a\vert$ |
- id:: 65fca23f-23b1-473d-b804-8bd3c2d316f7