public:: true
alias:: 无限集, infinite, infinitely, 无限集合

- # Finite, Infinite, Countable, Uncountable set
	- ## Definition
		- For any [[positive]] [[integer]] $n$, let $J_n$ be the [[set]] whose elements are the integers $1, 2,\cdots, n$; let $\mathbb{N}$ be the set consisting of all positive integers. For any set $A$, we say:
			- (a) $A$ is [[finite]] if $A\sim J_n$ for some $n$ (the [[empty set]] is also considered to be finite).
			- (b) $A$ is [[infinite]] if $A$ is not [[finite]].
			- (c) $A$ is [[countable]] if $A\sim \mathbb{N}$.
			- (d) $A$ is [[uncountable]] if A is neither [[finite]] nor [[countable]].
			- (e) A is [[at most countable]] if A is [[finite]] or [[countable]].
		- For two finite sets $A$ and $B$, we evidently have $A\sim B$ ([[equivalent]]) if and only if $A$ and $B$ contain the same number of elements. 
		  For infinite sets, however, the idea of "having the same number of elements" becomes quite vague, whereas the notion of [[1-1 correspondence]] retains its clarity.
	- ## Theorem
		- 1. Every [[infinite]] [[subset]] of a [[countable set]] $A$ is countable.
			- The theorem shows that countable sets represent the ''smallest'' infinity: *No uncountable set can be a subset of a countable set*.
		- 2. Let ${E_n}$, $n = 1, ,2, 3, ... $, be a [[sequence]] of [[countable sets]], and put:
		  $$S = \bigcup_{n=1}^{\infty}E_n$$ 
		  Then $S$ is countable.
		- 3. Let $A$ be a [[countable set]], and let $B_n$ be the set of all n-[[tuples]]($a_1 , \cdots, a_n$), where $a_k\in A (k = 1, ..., n)$, and the elements $a_1 , \cdots, a_n$ need not be distinct. Then $B_n$ is countable.
		- 4. Let $A$ be the set of all [[sequences]] whose elements are the [[digits]] $0$ and $1$. This set $A$ is [[uncountable]].