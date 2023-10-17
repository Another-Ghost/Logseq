alias:: 序列, sequences

- # Definition
	- By a [[sequence]], we mean a function $f$ defined on the [[set]] $N$ of **all**
	  [[positive]] [[integers]].
	  If $f(n) = x_n$, for $n\in N$, it is customary to denote the sequence $f$ by the symbol $\{x_n\}$, or sometimes by $x_1, x_ 2 , x_3 , \cdots$.
	  The values of the elements $x_n$ are called the [[terms]] of the sequence. 
	  If $A$ is a [[set]] and if $x_n\in A$ for all $n\in N$, then $\{x_n\}$ is said to be a [[sequence]] in $A$, or a sequence of [[elements]] of $A$.
		- Note that the terms $x_1, x_2, x_3, \cdots$ of a sequence *need not* be [[distinct]].
- # Sequences in Signal Processing
	- 在许多情形中, [[信息]]被表示成[[符号]]的[[序列]]。
	  logseq.order-list-type:: number
	  这些[[序列]]可以按两种方式出现。一种以[[数据]]的表示形式出现, 另一种则以[[事件流]]的表示形式出现。
	  事实上, [[序列]]是[[函数]]的特殊种类。
	- 一般而言, [[数据序列]]是如下形式的函数:
	  logseq.order-list-type:: number
	  $$Data: Indices → Symbols\tag{1}$$
	  其中 $Indices\subset Naturals$ , $Naturals$ 是一个[[自然数]]集合, $Indices$ 是一个合适的[[序号集]], 如 ${1,2,\cdots,N}$ , 而 $Symbols$ 也是一个合适的[[符号集]] 。
	- 第二种表示[[信息]]的方式是[[事件流]], 它用于[[序列]]出现的事件中。
	  logseq.order-list-type:: number
	  id:: 650ef98a-6a09-4ed2-ad8a-692120753a86
	  [[事件流]],或[[跟踪]], 是一个对发生在我们所关心的[[系统]]中的**重要事件的记录**。
	  事件流也是如同 $(1)$ 一样形式的函数。
-
-