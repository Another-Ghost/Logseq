alias:: rules of inference

- Inference rules are denoted by $I$ in [[proof]].
- # Inference Rules in [[Propositional Calculus]]
	- |永真式|名称|
	  |--|--|
	  |$G\wedge H\Rightarrow G;\ G\wedge H\Rightarrow H$|[[化简律]]|
	  |$G ⇒ G ∨ H;\ H ⇒ G ∨ H$|[[附加律]]|
	  |$G, H ⇒ G ∧ H$|[[合取引入]]|
	  |$G ∨ H, ¬G ⇒ H; \ G ∨ H, ¬H ⇒ G$|[[disjunctive syllogism]]|
	  |$G → H, G ⇒ H$|[[假言推理]]|
	  |$G → H, ¬H ⇒ ¬G$|[[否定后件式]]|
	  |$G → H, H → I ⇒ G → I$|[[hypothetical syllogism]]|
	  |$G ∨ H, G → I, H → I ⇒ I$|[[二难推论]]|
	- ## [[规则P]]
	  在推导的过程中，可随时引入[[premise]]集合中的任意一个前提；称为[[前提引用规则]]。
	- ## [[规则T]]
	  在推导的过程中，可以随时引入公式$S$，该公式 $S$是由其前的一个或多个公式推导出来的[[逻辑结果]]。称为[[逻辑结果引用规则]]。
	- ## [[规则CP]]
	  如果能从给定的前提集合$Γ$与公式$P$推导出$S$（把$P$当作附加前提），则能从此前提集合$Γ$推导出$P → S$。
	  原理：$P → (Q → R) = (P ∧ Q) → R$。
-
- # Inference Rules in [[Predicate Calculus]]
  假设$G(x), H(x)$是只含[[自由变元]]$x$的[[公式]]，则在[[全总个体域]]中，有：
	- $$ ∀xG(x) ⇒ ∃xG(x)$$
	- \begin{array}{}
	  ∀xG(x) ∨ ∀xH(x) ⇒ ∀x(G(x) ∨ H(x)) \\
	  ∃x(G(x) ∧ H(x)) ⇒ ∃xG(x) ∧ ∃xH(x)
	  \end{array}
	- \begin{array}{}
	  ∀xG(x) → ∀xH(x) ⇒ ∀x(G(x) → H(x)) \\
	  ∀x(G(x) → H(x)) ⇒ ∃xG(x) → ∃xH(x)
	  \end{array}
	- 对于多个量词的公式，设 G(x, y) 是含有自由变元 x, y 的谓词公式，则有
	  \begin{array}{}
	  ∃x∀yG(x, y) ⇒ ∀y∃xG(x, y) \\
	  ∀y∀xG(x, y) ⇒ ∃x∀yG(x, y) \\
	  ∀y∀xG(x, y) ⇒ ∃x∀yG(x, y) \\
	  ∃y∀xG(x, y) ⇒ ∀x∃yG(x, y) \\
	  ∀x∃yG(x, y) ⇒ ∃y∃xG(x, y) \\
	  ∀y∃xG(x, y) ⇒ ∃x∃yG(x, y)
	  \end{array}
	- ## [[全称特指规则]]
	  $∀xG(x) ⇒ G(y)$，$y$不在$G(x)$中[[约束出现]]。
	  或：
	  $∀xG(x) ⇒ G(c)$，$c$为*任意*[[个体常量]]。
	- ## [[存在特指规则]]
	  $∃xG(x) ⇒ G(c)$，$c$为使得$G(c)$为真的特定的[[个体常量]]  。
	  当$G(x)$中还有除$x$之外的[[自由变元]]，则必须用关于这些变元的[[函数符号]]来取代$c$。
	- ## [[全称推广规则]]
	  $G(y) ⇒ ∀xG(x)$，$G(y)$中无[[变元]]$x$。
	- ## [[存在推广规则]]
	  $G(c) ⇒ ∃xG(x)$，$c$为特定[[个体常量]]
	  或：
	  $G(y) ⇒ (∃x)G(x)$，$G(y)$中无[[变元]]$x$。
-
-
-