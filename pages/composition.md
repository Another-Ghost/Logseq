alias:: composite, 复合函数, 函数组合

- Suppose $X, Y, Z$ are metric spaces, $E\subset X$, $f$ [[maps]] $E$ into $Y$, $g$ maps the [[range]] of $f$, $f(E)$, into $Z$, and $h$ is the mapping of $E$ into $Z$ defined by 
  id:: 64816616-4658-4e7b-9915-598d0e16990f
  $$h(x) = g(f (x)),\quad (x\in E)$$
  This [[function]] $h$ is called the [[composition]] of $f$ and $g$, denoted by
  $$h= g\circ f$$
- # Theorem
	- Suppose $X, Y, Z$ are metric spaces, $E\subset X$, $f$ [[maps]] $E$ into $Y$, $g$ maps the [[range]] of $f$, $f(E)$, into $Z$, and $h$ is the **composition** of $f$ and $g$.
	  logseq.order-list-type:: number
	  If $f$ is [[continuous]] at a point $p\in E$ and if $g$ is continuous at the point $f(p)$, then $h$ is continuous at $p$.
- ## [[复合函数的求导法则]]