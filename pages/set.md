alias:: 集合

- # Definition
	- ## 朴素集合论
		- [[集合]]是指具有某种特定性质的事物的总体。集合里的事物称作[[元素]]。
		- 若$a$是集合$A$的元素，则称$a$属于$A$，记作$x\in A$。
		- 若$x$不是集合$A$的元素，，则称$a$不属于$A$，记作$x\notin A$。
		- 集合$A$中的元素个数称为集合的[[基数]]，记为$\left |A\right |$。
		- 若一个集合的基数是有限的，称该集合为[[有限集]]。
		- 若一个集合的基数是无限的，称该集合为[[无限集]]。
-
	- ## [[公理化集合论]]
	- # Operations
		- Let $A$ and $\Omega$ be sets, and suppose that with each *element* $\alpha$ of $A$ there is associated a *subset* of $\Omega$ which we denote by $E_\alpha$.
		  id:: 64777832-6f4e-4953-8658-40d62a06669a
		- The set whose elements are the sets $E_\alpha$ will be denoted by $\{E_\alpha\}$. Instead of speaking of sets of sets, we shall sometimes speak of a [[collection]] of sets.
		  id:: 64ab9216-a97a-47eb-8558-2a916670f99d
		- ## [[union]]
			- The [[union]] of the sets $E_\alpha$ is defined to be the set $S$ such that $x\in S$ if and only if $x\in E_\alpha$ for at least one $\alpha\in A$. We use the notation:
			  $$S=\bigcup_{\alpha\in A}E_\alpha$$
			  If $A$ consists of the [[integers]] $1, 2, ... , n$, one usually writes
			  $$S=\bigcup_{m=1}^{n}E_m$$
		- ## [[intersection]]
			- The [[intersection]] of the sets $E_\alpha$ is defined to be the set $P$ such that $x\in P$ if and only if $x\in E_\alpha$ for every $\alpha\in A$. We use the notation:
			  $$P=\bigcap_{\alpha\in A}E_\alpha$$
		- ## [[difference]]
		- ## [[symmetric difference]]
		- ## [[complement]]
			- ### Theorem
			  Let  $\left\{E_{\alpha}\right\}$  be a ([[finite]] or [[infinite]]) collection of sets  $E_{\alpha}$.Then 
			  $$\left(\bigcup_{\alpha}E_{\alpha}\right)^{c}=\bigcap_{\alpha}\left(E_{\alpha}^{c}\right)$$
		- ## Basic Equations
		  Let $U$  be the [[universal set]], $A,B,C$ be any set, then
			- 1. $A ∪ A = A, A ∩ A = A$. ([[幂等律]])
			  2. $A ∪ B = B ∪ A, A ∩ B = B ∩ A$. ([[交换律]])
			  3. $A ∪ (B ∪ C) = (A ∪ B) ∪ C, A ∩ (B ∩ C) = (A ∩ B) ∩ C$. ([[结合律]])
			  4. $A ∪ \phi = A, A ∩ U = A$. ([[同一律]])
			  5. $A ∪ U = U, A ∩ \phi = \phi$. ([[零律]])
			  6. $A ∪ (B ∩ C) = (A ∪ B) ∩ (A ∪ C), A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C)$. ([[分配律]])
			  7. $A ∪ (A ∩ B) = A, A ∩ (A ∪ B) = A$. ([[吸收律]])
			  8. $\overline{A} ∩ A = \phi, \overline{A} ∪ A = U$. ([[矛盾律]]和[[排中律]])
			  9. $\overline{\overline{A}} = A$. ([[双重否定律]])
			  10. $\overline{A \cup B}=\overline{A} \cap \overline{B}, \overline{A \cap B}=\overline{A} \cup \overline{B}$. ([[德摩根律]])
- # [[集合的划分]]
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
-