alias:: scalar product, 内积

- # Definition
	- [[内积]]是一种定义在某个[[向量空间]] \( V \) 上的[[二元运算]]，它将两个向量映射到一个标量。这个运算满足以下性质：
	  logseq.order-list-type:: number
		- **[[共轭对称性]]**：
		  logseq.order-list-type:: number
		   \[ \langle \mathbf{u}, \mathbf{v} \rangle = \overline{\langle \mathbf{v}, \mathbf{u} \rangle} \]
		   其中 \(\overline{z}\) 表示复数 \(z\) 的共轭。
		- **[[线性]]**：
		  logseq.order-list-type:: number
		   对于所有向量 \(\mathbf{u}, \mathbf{v}, \mathbf{w} \in V\) 和所有标量 \(\alpha\)：
		   \[ \langle \alpha \mathbf{u} + \mathbf{v}, \mathbf{w} \rangle = \alpha \langle \mathbf{u}, \mathbf{w} \rangle + \langle \mathbf{v}, \mathbf{w} \rangle \]
		- **[[正定性]]**：
		  logseq.order-list-type:: number
		   对于所有非零向量 \(\mathbf{v} \in V\)：
		   \[ \langle \mathbf{v}, \mathbf{v} \rangle > 0 \]
		   并且对于零向量 \(\mathbf{0}\)：
		   \[ \langle \mathbf{0}, \mathbf{0} \rangle = 0 \]
	- [[实数域]]上的一个[[正定]]的[[对称双线性函数]] $f$ 称为 $V$ 上的一个[[内积]].
	  logseq.order-list-type:: number
	  把 $f(\alpha, \beta)$ 简记成 $(\alpha, \beta)$ .
		- 由[[内积]]在一个[[基]]下的[[度量矩阵]]是[[正定矩阵]]可知: [[内积]]是[[非退化]]的[[对称双线性函数]] .
- >内积不仅限于实数或复数向量空间的元素，而且可以扩展到函数空间。例如，在 \( L^2 \) 空间（平方可积函数空间）中，两个函数 \( f \) 和 \( g \) 的内积定义为它们的积的积分：
  $$ \langle f, g \rangle = \int f(x) \overline{g(x)} \, dx $$
  这种定义允许我们在更广泛的数学和物理领域内使用内积的概念，例如在信号处理中。