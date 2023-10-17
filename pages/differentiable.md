alias:: first order approximation, differentiability, 可导, 可微, 可微函数, 可微性

- >See [[derivative of real function]]
- > If $f$ is [[differentiable]] at $c$, we have
  $$f^\prime(c)=\lim_{x\to c}\frac{f(x)-f(c)}{x-c}$$
  $$\lim_{x\to c}\left[\frac{f(x)-f(c)}{x-c}-f^\prime(c)\right]=0$$
  $$\lim_{x\to c}\frac{f(x)-\left[f(c)+f^{\prime}(c)(x-c)\right]}{x-c} =0$$
   Then $\exists \phi:(a, b) \rightarrow R$ 
  $$\phi(x)=\frac{f(x)-\left[f(c)+f^{\prime}(c)(x-c)\right]}{x-c}$$
  which is [[continuous]] at $c$ such that
  $$f(x)=f(c)+f^{\prime}(c)(x-c)+(x-c) \phi(x)$$
  for all  $x \in(a, b)$, with $\phi(c)=0$.