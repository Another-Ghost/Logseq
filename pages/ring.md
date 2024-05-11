public:: true
alias:: 环

- ## 定义
	- 设$R$是一个非空[[set]]，如果它有两个[[代数运算]]，一个叫做[[加法]]，记作$a+b$，另一个叫做[[乘法]]，记作$ab$；并且这两个运算满足下列6条运算法则（$\forall a,b,c,d\in R$）:
	  logseq.order-list-type:: number
		- [[加法结合律]]，即$(a+b)+c=a+(b+c)$；
		  logseq.order-list-type:: number
		- [[加法交换律]]，即$a+b=b+a$；
		  logseq.order-list-type:: number
		- 在 $R$ 中有元素 $0$，使得 $a+0=a$，称 $0$ 是 $R$ 的[[零元]]；
		  logseq.order-list-type:: number
		- 对于$a$，在$R$中有元素 $d$，使得 $a+d=0$，称 $d$ 是 $a$ 的[[负元]]，记作 $-a$；
		  logseq.order-list-type:: number
		- [[乘法结合律]]，即$(ab)c=a(bc)$；
		  logseq.order-list-type:: number
		- 乘法对于加法的左，右[[分配律]]，即：
		  logseq.order-list-type:: number
		  $$a(b+c)=ab+ac$$
		  $$(b+c)a=ba+ca$$
		- 那么称$R$是一个[[ring]]。
		- 容易证明，环$R$中的[[零元]]是 *唯一* 的；R中的元素$a$的[[负元]]是 *唯一* 的：$-(-a)=a$。
		- 环$R$中可以定义[[减法]]：
		  $a-b :=a+(-b)$
	- $\boldsymbol{Z}$，$2\boldsymbol{Z}$，$K[x]$，$M_n[K]$都是[[环]]，分别称为[[整数环]]，[[偶数环]]，数域$K$上[[一元多项式环]]，数域 $K$ 上$n$级[[全矩阵环]]。
	  logseq.order-list-type:: number
	  任意一个[[数域]]$K$也是环。
	- 若环$R$中有一个元素$e$具有性质：
	  logseq.order-list-type:: number
	  $$ea=ae=a,\forall a\in R$$
	  则称$e$是$R$的[[单位元]]，此时称$R$是[[有单位元的环]]。
		- 容易证明，在有单位元的环$R$中，[[单位元]]是唯一的，通常把单位元记成$1$。
	- 对于$a\in R$，如果存在$b\in R$且$b\ne 0$，使得$ab=0$（或$ba=0$），那么称$a$是一个[[左零因子]]（或[[右零因子]]），通称为[[零因子]]。
	  logseq.order-list-type:: number
		- 环$R$中，$0a=a0=0,\forall a\in R$，从而$0$既是左零因子，又是右零因子，称$0$是[[平凡的零因子]]，其余的零因子称为[[非平凡的零因子]]。
	- 若环$R$到环$R^{'}$有一个[[bijection]]$\sigma$，满足：
	  logseq.order-list-type:: number
		- \begin{array}{c}\sigma(a+b)=\sigma(a)+\sigma(b),\forall a, b\in K\\ \sigma(ab)=\sigma(a)\sigma(b),\forall a,b\in K\end{array}
		- 则称$\sigma$是环$R$到$R^{'}$的一个[[同构映射]]。
		- 此时称环$R$与$R{'}$是[[同构]]的，记作$R\cong R^{'}$。