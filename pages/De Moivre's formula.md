alias:: 棣莫弗定理, 棣莫弗公式

- [[complex number]] $z$ use the form $z=r(\cos\theta+i\sin\theta)$, then we have
  id:: 64986f22-6386-41bf-ab71-f42ae92a34f5
  $$z^n=r^n(\cos{n\theta}+i\sin n\theta),n\in N^*$$
  As $r=\left |z\right |$, we have 
  $$\left |z^n\right |=r^n=\left |z\right |^n$$
- In [[exponential form of complex number]], it is
  $$(e^{i\theta})^n=e^{in\theta}$$
- # Proof
  Let $z_1=r_1(\cos\theta_1+i\sin\theta_1)$, $z_2=r_2(cos\theta_2+i\sin\theta_2)$.
  Then
  \begin{aligned}
  z_1z_2 &=r_1r_2(cos\theta_1+i\sin\theta_1)(\cos\theta_2+i\sin\theta_2) \\
  &=r_1r_2[\cos\theta_1\cos\theta_2+i(\sin\theta_1\cos\theta_2+\cos\theta_1\sin\theta_2)-\sin\theta_1\sin\theta_2] \\
  &=r_1r_2[\cos(\theta_1+\theta_2)+i\sin(\theta_1+\theta_2)]
  \end{aligned}
  If we have $z_1=r_1(\cos\theta_1+i\sin\theta_1),z_2=r_2(cos\theta_2+i\sin\theta_2),\cdots, z_n=r_n(\cos\theta_n+i\sin\theta_n)$
  then
  $$z_1z_2\cdots z_n = r_1r_2\cdots r_n[\cos(\theta_1+\theta_2+\cdots+\theta_n)+i\sin(\theta_1+\theta_2+\cdots+\theta_n)]$$
  Take $z_1=z_2=\cdots=z_n$, we get
  $$z^n=r^n(\cos{n\theta}+i\sin n\theta)$$