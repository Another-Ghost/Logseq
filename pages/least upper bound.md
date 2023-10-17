alias:: supremum, 最小上界, 上确界, sup

- # definition
	- Suppose $S$ is an [[ordered set]], $E\in S$, and $E$ is [[bounded above]]. Suppose there exists an $\alpha\in S$ with the following properties:
	  id:: 6434c113-dabe-4097-8705-2bbba5f7c5c7
		- (i) $\alpha$ is an [[upper bound]] of $E$.
		- (ii) If $\gamma < \alpha$ then $\gamma$ is not an upper bound of $E$.
		  id:: 645d5076-d621-4ac3-a1d7-80e4ea110386
	- Then $\alpha$ is called the [[least upper bound]] of $E$ [that there is at most one such $\alpha$ is clear from (ii)] or the [[supremum]] of $E$, and we write
	  $$\alpha=\mathrm{sup}\ E.$$
- An ordered set is said to have the [[least-upper-bound property]] if the following is true:
  if ($\forall$)$E\subset S$, $E\ne \emptyset$, and $E$ is [[bounded above]], then $\mathrm{sup}\ E$ exists in $S$.