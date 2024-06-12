alias:: 协方差

- ## 定义
- 设 $(X, Y)$ 是二维随机变量，如果 $E\{[X-E(X)][Y-E(Y)]\}$ 存在，则称
  $$\operatorname{cov}(X, Y) \triangleq E\{[X-E(X)][Y-E(Y)]\}$$
  为随机变量 $X$ 和 $Y$ 的^^协方差^^。
- 在实际计算协方差时，更多的是使用以下公式
  $$\operatorname{cov}(X, Y)=E(X Y)-E(X) E(Y)$$
  这是因为
  $$\begin{aligned}
  \operatorname{cov}(X, Y) & =E\{[X-E(X)][Y-E(Y)]\} \\
  & =E[X Y-X E(Y)-Y E(X)+E(X) E(Y)] \\
  & =E(X Y)-E[X E(Y)]-E[Y E(X)]+E[E(X) E(Y)] \\
  & =E(X Y)-E(X) E(Y)-E(Y) E(X)+E(X) E(Y) \\
  & =E(X Y)-E(X) E(Y) .
  \end{aligned}$$
- 协方差反映了 $X$ 和 $Y$ 之间的关系：可设 $Z=[X-E(X)][Y-E(Y)]$ ， $\operatorname{cov}(X$ , $Y)=E(Z)$。
	- 若 $\operatorname{cov}(X$ ,$Y)>0$ ，事件 $\{Z>0\}$ 更有可能发生，即事件 $\{X>E(X)\} \cap \{Y>E(Y)\}$ 或 $\{X<E(X)\} \cap\{Y<E(Y)\}$ 发生的可能性更大，说明 $X$ 和 $Y$ **均有同时大于或同时小于各自平均值的趋势**；
	- 若 $\operatorname{cov}(X$ , $Y)<0$ ，事件 $\{Z<0\}$ 更有可能发生，即事件 $\{X> E(X)\} \cap\{Y<E(Y)\}$ 或 $\{X<E(X)\} \cap\{Y>E(Y)\}$ 发生的可能性更大，说明 $X$ 和 $Y$ 中**有一个有大于其平均值的趋势另一个有小于其平均值的趋势**。
- 所以说协方差反映了随机变量 $X$ 和 $Y$ 之间“协同”变化的关系 $.$ 当 $Y$ 就是 $X$ 时， $\operatorname{cov}(X$ ， $Y)=\operatorname{cov}(X$ ， $X)=D(X)$ 协方差即为[[方差]]，这就是我们称其为协方差的原因 $.$
- ## 性质
  设 $X$ ， $Y$ ， $X_{1}$ 与 $X_{2}$ 为任意的随机变量， $c$ ， $k$ 和 $l$ 为常数，则有
	- logseq.order-list-type:: number
	  $$\operatorname{cov}(X, c)=0$$
	- logseq.order-list-type:: number
	  $$\operatorname{cov}(X, Y)=\operatorname{cov}(Y, X) ;$$
	- logseq.order-list-type:: number
	  $$\operatorname{cov}(k X, l Y)=k l \operatorname{cov}(X, Y) ;$$
	- logseq.order-list-type:: number
	  $$\operatorname{cov}\left(X_{1}+X_{2}, Y\right)=\operatorname{cov}\left(X_{1}, Y\right)+\operatorname{cov}\left(X_{2}, Y\right) .$$
		- 利用[[期望]]的性质证明