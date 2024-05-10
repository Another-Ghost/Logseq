alias:: compact, 紧集, compact sets, compactness

- # Definition
	- A **subset** $K$ of a [[metric space]] $X$ is said to be [[compact]] if every [[open cover]] of $K$ contains a [[finite]] [[subcover]].
		- >More explicitly, if $\{G\alpha\}$ is an open cover of $K$, then there are **finitely** many indices $\alpha_1,\cdots,\alpha_n$ such that 
		  $$K\subset \bigcup_{i=1}^{n}G_{\alpha_i}$$
		- <!-- the number of points in a compact set is infinite, but the number of neighborhood(with $r=\varepsilon_n$) of points that cover the compact set is finite.
		  证明的过程中通常要取$\varepsilon_n$的minimum。
		  -->
- # Theorem
	- 1. Suppose $K\subset Y\subset X$. Then $K$ is compact relative to $X\Longleftrightarrow K$ is compact relative to $Y$.
	- 2. Compact subsets of metric spaces are [[closed]].
	- 3. [[Closed]] **subsets** of compact sets are compact.
		- ## Carollary
		  If $F$ is closed and $K$ is compact, then $F\cap K$ is compact.
	- 4. If $\{K_\alpha\}$ is a [[collection]] of compact subsets of a metric space $X$ *such that* the [[intersection]] of **every** [[finite]] [[subcollection]] of $\{K_\alpha\}$ is **nonempty**, then $\bigcap K_\alpha$ is **nonempty**.
	- 5. If $E$ is an [[infinite]] **subset** of a compact set $K$, then $E$ has a [[limit point]] in $K$.
	  6. If $\{I_n\}$ is a [[sequence]] of [[closed]] [[intervals]] in $R^1$ , such that $I_n\supset I_{n+1} (n = 1, 2, 3, \cdots)$ (nested), then $\bigcap_1^{\infty}I_n$ is **not empty**.
	- 7. Let $k$ be a [[positive]] [[integer]]. If $\{I_n\}$ is a sequence of [[k-cells]] such that $I_n\supset I_{n+ 1} (n = I, 2, 3, \cdots)$, then $\bigcap_1^\infty I_n$ is not empty.
	- 8. Every [[k-cell]] is [[compact]].
	- 9. If a set $E\subset R^k$ has one of the following three properties, then it has the other two:
		- (a) $E$ is [[closed]] and [[bounded]].
		- (b) E is [[compact]].
		- (c) Every [[infinite]] **subset** of $E$ has a [[limit point]] in $E$.
		- >The [[equivalence]] of (a) and (b) is known as [[Heme-Borel theorem]].
		- >(b) and (c) are equivalent in **any** [[metric space]] (Exercise 26)
		  but that (a) does **not**, in general(besides in [[euclidean space]] $R^k$), **imply** (b) and (c).
	- 10. [[Bolzano-Weierstrass theorem]]
	  Every [[bounded]] [[infinite]] **subset** of $R^k$ has a [[limit point]] in $R^k$.
-