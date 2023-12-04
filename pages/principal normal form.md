# [[principal conjunctive normal form]]
- # [[principal disjunctive normal form]]
- # 主范式求解定理
	- 1. 求出该公式所对应的[[析取范式]]或[[合取范式]]；
	  2. 消去重复出现的[[命题变元]]，[[矛盾式]]或[[重言式]]；可使用如下公式：
	  {{embed ((bd5aca2d-f9f1-49a0-ad81-40ebe238d804))}}
	  {{embed ((152bc213-c1d4-4d64-9be0-4d23f095f2f1))}}
	  {{embed ((eea96ce9-91ca-44c6-9f0c-8b74ab1913ac))}}
	  {{embed ((df3dc3dc-4e4f-4117-9330-e97b80ae533c))}}
	  {{embed ((829ec58d-fdf5-4499-907f-0cd390af7e51))}}
- 3. 若析取（合取）范式的某一个[[短语]]（[[子句]]）$b_i$中缺少命题变元$p$，则可用如下方式将$p$补进去：
  $$b_i = b_i ∧ 1 = b_i ∧ (¬p ∨ p) = (b_i ∧ ¬p) ∨ (b_i ∧ p)$$
  $$b_i = b_i ∨ 0 = b_i ∨ (¬p ∧ p) = (b_i ∨ ¬p) ∧ (b_i ∨ p)$$
  重复至所有短语或子句都是[[极小项]]或[[极大项]]为止。
- 4. 利用
  {{embed ((bd5aca2d-f9f1-49a0-ad81-40ebe238d804))}}
  将重复的极小项和极大项合并，并利用
  {{embed ((2c22a1da-d086-4bb1-8b4b-8057100cd2fe))}}
  进行顺序调整，由此可转换成标准的[[主析取范式]]和[[主合取范式]]。