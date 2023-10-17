## [[偏手性]]
	- 对于[[模型空间]]和[[世界空间]], [[Unity]]使用的是[[左手坐标系]];
	  对于[[观察空间]], *Unity* 使用的是[[右手坐标系]].
- ## 行矩阵还是列矩阵
	- 在[[Unity]]中, 常规做法是把[[矢量]]放在[[矩阵]]的右侧，即把 *矢量* 转换成[[列矩阵]]来进行计算。
	  这意味着，我们的[[矩阵乘法]]通常都是[[右乘]].
	  例如 
	  $$\boldsymbol{CBA}\bold{v}=(\boldsymbol{C}(\boldsymbol{B}(\boldsymbol{A}\bold{v}))$$
- # [[旋转顺序]]
	- ## 两种类型旋转顺序
		- 旋转是始终初始的[[坐标系]];
		  logseq.order-list-type:: number
		- 绕一个轴旋转后，在新的 *坐标系* 下进行[[旋转]].
		  logseq.order-list-type:: number
	- *Unity* 中，[[旋转顺序]]是指 *第一种旋转顺序*, 为 $zxy$ ，用[[旋转变换矩阵]]表示为：
	  $$\boldsymbol R_z\bold R_x\bold R_y$$
-