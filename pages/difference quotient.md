alias:: 差商, 均差

- ## Definition
	- 对于[[函数]] \( f : \mathbb{R} \to \mathbb{R} \)，[[差商]]定义为：
	  logseq.order-list-type:: number
	  $$ Q(h) = \frac{f(x+h) - f(x)}{h}, \quad h \neq 0 $$
	  其中，\( x \in \mathbb{R} \) 且 \( h \in \mathbb{R} \setminus \{0\} \)。
	  差商 \( Q(h) \) 描述了函数 \( f \) 在区间 \([x, x+h]\) 上的平均变化率。
	- 函数 \( f \) 在 \( x \) 处的[[导数]]，记为 \( f'(x) \) 或 \( \frac{df}{dx}(x) \)，定义为差商 \( Q(h) \) 当 \( h \to 0 \) 时的极限（如果该极限存在）：
	  logseq.order-list-type:: number
	  $$ f'(x) = \lim_{h \to 0} Q(h) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h} $$