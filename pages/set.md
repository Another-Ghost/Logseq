public:: true
alias:: 集合

- # Definition
	- ## [[朴素集合论]]
		- [[集合]]是指具有某种特定性质的事物的总体。集合里的事物称作[[元素]]。
		- 若$a$是集合$A$的元素，则称$a$属于$A$，记作$x\in A$。
		- 若$x$不是集合$A$的元素，，则称$a$不属于$A$，记作$x\notin A$。
		- 集合$A$中的元素个数称为集合的[[基数]]，记为$\left |A\right |$。
		- 若一个集合的基数是有限的，称该集合为[[有限集]]。
		- 若一个集合的基数是无限的，称该集合为[[无限集]]。
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
-