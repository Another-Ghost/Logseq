alias:: 域
title:: field

- # Definition
	- A [[field]] is a [[set]] $F$ with two [[operation]]s, called [[addition]] and [[multiplication]], which satisfy the following so-called [[field axioms]] (A), (M), and (D):
	  logseq.order-list-type:: number
		- (A) Axioms for [[addition]]
			- (A1) If $x\in F$ and $y\in F$, then their [[sum]] $x + y$ is in $F$.
			- (A2) Addition is [[commutative]]: $x + y = y + x$ for all $x, y\in F$.
			- (A3) Addition is [[associative]]: $(x + y) + z = x + (y + z)$ for all $x, y, z\in F$.
			- (A4) $F$ contains an [[element 0]] such that $0 + x = x$ for every $x\in F$.
			- (A5) To every $x\in F$ corresponds an element $-x\in F$ such that
			- $$x +(-x) = 0.$$
		- (M) Axioms for [[multiplication]]
			- (M1) If $x\in F$ and $y\in F$, then their [[product]] $xy$ is in F.
			- (M2) Multiplication is [[commutative]]: $xy = yx$ for all $x, y\in F$.
			- (M3) Multiplication is [[associative]]: $(xy)z = x(yz)$ for all $x, y, z\in F$.
			- (M4) F contains an [[element 1]]$\ne 0$ such that $1x= x$ for every $x\in F$.
			- (M5) If $x\in F$ and $x\ne 0$ then there exists an element $1/x\in F$ such that $x·(1/x)=1$.
		- (D) the [[distributive law]]
			- $$x(y + z) = xy + xz$$
			- holds for all $x, y, z\in F$.
	- 另一种定义：
	  logseq.order-list-type:: number
	  一个有[[单位元]]$1(\ne 0)$ 的[[交换环]]$F$, 如果他的每个 *非*[[零元]] 都是[[可逆元]], 那么称 $F$ 是一个[[域]].
- # Remarks
	- (a) One usually writes (in any field)
	  $$x-y, \frac{x}{y}, x + y + z, xyz, x^2, x^3, 2x, 3x, ...$$
	  in place of
	  $$x+(-y), x\cdot\frac{1}{y}, (x+y)+z, (xy)z, xx, xxx, x + x, x + x + x, ....$$
- # Proposition
	- The axioms for addition imply the following statements.
		- (a) If $x + y = x + z$ then $y = z$.
		- (b) If $x + y = x$ then $y = 0$.
		- (c) If $x + y = 0$ then $y = - x$.
		- (d) $-(-x) = x$.
		- Statement (a) is a [[cancellation law]]. Note that (b) asserts the [[uniqueness]] of the element whose existence is assumed in (A4), and that (c) does the same for (A5).
	- The axioms for multiplication imply the following statements.
		- (a) If $x\ne 0$ and $xy = xz$ then $y = z$.
		- (b) If $x\ne 0$ and $xy = x$ then $y = 1$.
		- (c) If $x\ne 0$ and $xy = 1$ then $y = 1/x$.
		- (d) If $x\ne 0$ then $1/(1/x) = x$.
		- The proof is so similar to that of Proposition of the axioms for addition that we omit it.
	- The field axioms imply the following statements, for any $x, y, z\in F$.
		- (a) $0x= 0$.
		- (b) If $x\ne 0$ and $y\ne 0$ then $xy\ne 0$.
		- (c) $(-x)y = -(xy) = x(-y)$.
		- (d) $(-x)(-y) = xy$.
-