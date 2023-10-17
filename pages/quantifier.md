alias:: 量词, quantifiers

- # [[universal quantifier]]
- # [[existential quantifier]]
- # [[uniqueness quantifier]]
- 在$∀xF(x)$，$∃xF(x)$中的 x 称为[[作用变量]]。一般将其量词加在其[[谓词]]之前。此时，F(x)称为全称量词和存在量词的[[restricted domain]]。
-
- # 谓词逻辑符号化的规则
	- 统一[[domain of discourse]]为[[universe of discourse]]，而对每一个句子中[[个体变量]]的变化范围用一元[[特性谓词]]刻划之。这种特性谓词在加入到[[命题函数]]中时必定遵循如下原则：
		- 对于全称量词$(∀x)$，刻划其对应个体域的特性谓词作为[[蕴涵式]]之[[前件]]加入。
		- 对于存在量词$(∃x)$，刻划其对应个体域的特性谓词作为[[合取式]]之合取项加入。
	- 如：
		- 所有的老虎都要吃人；
		  $P(x):x$要吃人。$(∀x)P(x),x ∈\{老虎\}$
		- 有一些人登上过月球；
		  $R(x):x$登上过月球。$(∃x)R(x),x ∈\{人\}$
	- 以上符号化必须要特别注明个体域，在表达比较复杂的命题时会容易混淆。转为用特性谓词刻化后：
		- $T(x):x$是老虎，$P(x):x$要吃人。$(∀x)(T(x) → P(x))$
		- $H(x):x$是人，$R(x):x$登上过月球。$(∃x)(H(x) ∧ R(x))$
- # Order of Quantifiers
	- The *order* of nested quantifiers *matters* if quantifiers are of *different type*.
		- $\forall x\exist y L(x,y)$ is not the same as $\exist y\forall x L(x,y)$
	- The *order* of nested quantifiers *does not matter* if quantifiers are of the *same type*.
-