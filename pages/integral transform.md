alias:: 积分变换, 积分转换

- # Definition
	- 以一[[变数]]为 $t$ 的[[函数]] $f(t)$ 为例，$f(t)$ 经过一[[积分转换]] $T$ 得到 $Tf(u)$ :
	  logseq.order-list-type:: number
	  $$
	  (Tf)(u)=\displaystyle\int\limits_{t_1}^{t_2}K(t,u)f(t)dt
	  $$
	  其中 $K$ 是个确定的[[二元函数]], 称为此[[积分变换]]的[[核函数]] 或[核]([[核函数]])。
	  当选取不同的[[积分域]]和[[变换核]]时，就得到不同名称的[[积分变换]]。
	  $f(t)$ 称为[[象原函数]]，$Tf(u)$ 称为 $f(t)$ 的[[象函数]]，在一定条件下，它们是[[一一对应]]而 *变换* 是[[可逆]]的.
	- 有些[[积分变换]]有相对应的[[反积分变换]]，使得
	  logseq.order-list-type:: number
	  $$
	  f(t)=\intop_{u_1}^{u_2}K^{-1}\left(u,t\right)\left(Tf\right)\left(u\right)du
	  $$
	  而 $K^{-1}(u,t)$ 称为[[反核]].