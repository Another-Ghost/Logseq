alias:: 群

- ## 定义
- ### 乘法群
	- 若[[集合]] $G \neq \varnothing$ ，在 $G$ 上的[[二元运算]]（该运算称为[[群的乘法]]，其结果称为[[积]]）
	  $$\cdot: G \times G \rightarrow G$$ 
	  构成的[[代数结构]]（ $G$ ， $\cdot$ ），满足：
		- [[封闭性]]：即 $G$ 的任意两个元素在 $\cdot$ 下的运算结果都是该集合的一个元素。（ $\forall a$ ， $b \in G$ ， $a \cdot b \in G$ ）；
		  logseq.order-list-type:: number
		- [[结合律]]： $\forall a$ ， $b$ ， $c \in G$ ，有 $(a \cdot b) \cdot c=a \cdot(b \cdot c)$ ；
		  logseq.order-list-type:: number
		- [[单位元]]： $G$ 中存在元素 $e$ ，使 $\mathrm{G}$ 中任意元素 $a$ 与之相乘（包括左乘和右乘）的结果都等于 $a$ 本身。 $( \exists e \in G$ 使 $\forall a \in G$ ，有 $e \cdot a=a \cdot e=a$ ）；
		  logseq.order-list-type:: number
		- [[逆元]]： $\forall a \in G$ ， $\exists b \in G$ ，使得 $a \cdot b=b \cdot a=e$ ， $b$ 称为 $a$ 的逆元，记为 $a^{-1}$ ，
		  logseq.order-list-type:: number
	- 则 $(G, \cdot)$ 称为一个^^群^^，或[[乘法群]]，简记作 $G$ 。
	- 在无歧义时，可将 $a \cdot b$ 写成 $a b$ 。
- ### 加法群
	- 有时由于上下文的原因，群上的二元运算亦可称为[[群的加法]]，此时该运算通常记为 $+$ ，群元素的运算也被记为如同 $a+b$ 的形式，而群也可被称为[[加法群]]。
- ## 性质
  设 $G$ 是一个群，则
	- [[单位元]]是**唯一**的：设 $e$ 和 $f$ 都是 $G$ 的单位元，则根据定义中的 $3$ ，有 $e=e f=f .$
	  logseq.order-list-type:: number
	- 任意一个元素的[[逆元]]是**唯一**的：设 $b$ 和 $c$ 都是 $a$ 的逆元，根据定义中的 $2$ ， $3$ 和 $4$ ， $b=b e=b(a c)=(b a) c=e c=c .$ 
	  logseq.order-list-type:: number
	- 对任意 $a$ ， $b \in G$ ，[[方程]] $a x=b$ 和 $y a=b$（其中 $x$ ， $y$ 是未知数 $)$ 在 $G$ 中都有[[解]]，此时 $x=a^{-1} b$ ， $y=b a^{-1}$ 。
	  logseq.order-list-type:: number
		- ### 证明
		  根据定义 $4$ ， $\exists a^{-1} \in G$ 使得 $a^{-1} a=e$ 。由于 $a^{-1}$ 和 $b$ 均为 $G$ 中元素并且 $G$ 关于乘法封闭，所以 $a^{-1} b$ 也在 $G$ 中。令 $x=a^{-1} b$ ，则 $a x=a\left(a^{-1} b\right)=\left(a a^{-1}\right) b=e b=b$ ，因此方程在 $G$ 中有解 $x=a^{-1} b$ 。同理可证另一个方程在 $G$ 中有解 $y=b a^{-1}$ 。
	- $G$ 满足[[消去律]]（[[左消去]]和[[右消去]]），即 $\forall a$ ， $b$ ， $c \in G$ ，若 $a b=a c$ ，则 $b=c$ ；若 $b a=c a$ ，则 $b=c$ 。
	  logseq.order-list-type:: number
	  collapsed:: true
		- 若 $a b=a c$ ，则两边左乘 $a^{-1}$ ，根据结合律即可得 $b=c$ ，同理可证右消去律。
		- #+BEGIN_NOTE
		  性质 $4$ 的消去律虽然是由逆元 $a^{-1}$ 的存在性以及单位元 $e$ 的存在性证明的，但是不能将定义中的 $3$ ：单位元的存在性和 $4$ ：逆元的存在性替换为消去律。例如考虑正整数集以及通常意义下的乘法，在乘法下正整数集满足封闭性、乘法结合律和消去律，但显然无法构成一个群，因为除了单位元“ $1$ ”以外所有元素都不存在逆元。
		  #+END_NOTE
		- 但是，如果将集合限定为有限集，则只要它满足封闭性、结合律和消去律，它就是一个群。
	- 任意一个元素的[[逆元]]的逆元是其本身，即 $\forall a \in G$ ， $\left(a^{-1}\right)^{-1}=a$
	  logseq.order-list-type:: number
		- 设 $b$ 是 $a^{-1}$ 的逆元，则 $b a^{-1}=e=a a^{-1}$ 。根据消去律可知 $b=a$ 。
	- 对任意 $a$ ， $b \in G$ ， $(a b)^{-1}=b^{-1} a^{-1}$ 。
	  logseq.order-list-type:: number
		- 由封闭性易证 $b^{-1} a^{-1} \in G$ 。由于 $b^{-1} a^{-1} a b=b^{-1}\left(a^{-1} a\right) b=b^{-1} e b=b^{-1} b=e$ ，所以 $b^{-1} a^{-1}$ 是 $a b$ 的逆元。根据逆元的唯一性可知结论成立。
- ## 例子
	- $G=\{1$ ， $-1\}$ 在普通乘法下是群。
	  logseq.order-list-type:: number
	  证：
		- 封闭性： $1 \times 1=1(-1) \times(-1)=1(-1) \times 1=-1 \quad 1 \times(-1)=-1$
		  logseq.order-list-type:: number
		- 结合律：成立
		  logseq.order-list-type:: number
		- 单位元： $1$ 
		  logseq.order-list-type:: number
		- 逆元素： $1$ 的逆元是 $1$ ， $-1$ 的逆元是 $-1$ 
		  logseq.order-list-type:: number
	- $G=\{0$ ， $1$ ， $2$ ， $\ldots \ldots$ ， $n-1\}$ 在 mod \mathrm{n} 的加法下是群
	  logseq.order-list-type:: number
	  证：
		- 封闭性：除以 $n$ 的余数只能是 $\{0$ ， $1$ ， $2$ ， $\ldots \ldots$ ， $n-1\}$ ，故封闭性成立
		  logseq.order-list-type:: number
		- 结合律：成立
		  logseq.order-list-type:: number
		- 单位元： $0$ 
		  logseq.order-list-type:: number
		- 逆元素：对任意元素 $\mathrm{a}$ 有 $[a+(n-a)] \bmod n=0$ ， $a$ 的逆元 $a^{-1}=n-a$
		  logseq.order-list-type:: number
	- ### [[置换群]]
	  logseq.order-list-type:: number
	- ### [[一般线性群]]
	  logseq.order-list-type:: number
- ## [[半群]]
- ## [[阿贝尔群]]
- ## [[群同态]]
	-