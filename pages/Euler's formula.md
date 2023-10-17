alias:: 欧拉公式

- # Theorem
	- In [[complex field]], For any [[real number]] $x$:
	  $$e^{ix}=\cos x+i\sin x$$
	  where $e$ is the [[Euler's number]], $i$ is the [[imaginary unit]], and $\cos$ and $\sin$ are the [[trigonometric functions]] [[cosine]] and [[sine]] respectively.
	  Take $x=\pi$,
	  \begin{array}{c}
	  e^{i\pi}=\cos\pi+i\sin\pi=-1 \\
	  e^{i\pi}+1=0 \\
	  i\pi = \ln(-1)
	  \end{array}
		- >$$e^{2k\pi}=1\quad(k=1,2,\cdots)$$
- # Proof
  let $z = a+bi \in \mathbb{C}$, $a, b\in\mathbb{R}$.
  By theorem {{embed ((647a0831-3568-4c89-943e-f53086620cab))}}
  we have
  \begin{aligned}
  \lim_{n\to\infty}\left(1+\frac{z}{n}\right)^n &= \lim_{n\to\infty}\left(\left(1+\frac{z}{n}\right)^\frac{n}{z}\right)^z \\
  &= \left(\lim_{n\to\infty}\left(1+\frac{z}{n}\right)^\frac{n}{z}\right)^z \\
  & = e^z 
  \end{aligned}
  That is
  $$e^{a+bi}=\lim_{n\to\infty}\left(1+\frac{a+bi}{n}\right)^n $$
  Let 
  $$\left(1+\frac{a+bi}{n}\right)^n=\left(\frac{n+a}{n}+\frac{b}{n}i\right)^n = r_n(\cos\theta_n+i\sin\theta_n)$$
  From [[De Moivre's formula]],
  $$r_n=\left[\left(1+\frac{a}{n}\right)^2+\left(\frac{b}{n}\right)^2\right]^\frac{n}{2}$$
  $$\theta_n=n\arctan\frac{b}{n+a}$$
  \begin{aligned}
  \lim_{n\to\infty}\ln r_n &=\lim_{n\to\infty}\frac{n}{2}\ln\left(1+\frac{2a}{n}+\frac{a^2+b^2}{n^2}\right)\quad \\
  &= \lim_{n\to\infty}\frac{n}{2}\left(\frac{2a}{n}+\frac{a^2+b^2}{n^2}\right) \\
  &= a
  \end{aligned}
  (Used [[Maclaurin series]] here).
  that is 
  $$\lim_{n\to\infty}r_n=e^a$$
  Then
  \begin{aligned}
  \lim_{n\to\infty}\theta_n&=\lim_{n\to\infty}n\arctan\frac{\frac{b}{n}}{1+\frac{n}{a}} \\
  &= \lim_{n\to\infty}\frac{bn}{n+a} \\
  &= b
  \end{aligned}
  (Also used [[Maclaurin series]] here).
  From above, we have
  \begin{aligned}
  e^{a+bi} &=\lim_{n\to\infty}(\frac{n+a}{n}+\frac{b}{n}i)^n \\
  &=\lim_{n\to\infty}r_n(\cos\theta_n+i\sin\theta_n) \\
  &=e^a(\cos b + i\sin b)
  \end{aligned}
  Take $a = 0$, 
  $$e^{bi}=\cos b+i\sin b$$
  Finally, we get
  $$e^{xi}=\cos x+i\sin x$$
-