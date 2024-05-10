alias:: 群同态

- 若对于两个[[群]]（ $G$ ， $\cdot$ ）和 $(H$ ， $\times)$ ，有[[映射]] $f$ ： $G \rightarrow H$ 满足以下条件：
  对 $G$ 中任意元素 $\mathrm{a}$ ， $\mathrm{b}$ ，都有 $f(a \cdot b)=f(a) \times f(b)$ ；
  则称映射 $f$ 为群（ $G$ ， $\cdot$ ）到群（ $H$ ， $\times$ ）的^^同态^^。
	- 如果映射 $f$ 为[[单射]]，则称 $f$ 为[[单同态]]。
	- 如果映射 $f$ 为[[双射]]，则称 $f$ 为[[同构]]。
- 易证得，同态有如下性质：
  $$f\left(e_{G}\right)=e_{H}$$
  其中 $e_{G}$ 是 $G$ 的[[单位元]]， $e_{H}$ 是 $H$ 的单位元。
- 经典的同态有
	- logseq.order-list-type:: number
	  $$f: \mathbb{Z} \mapsto \mathbb{Z}_{n}[\forall z(z \in \mathbb{Z} \rightarrow f(z)=z(\bmod n))]$$
	  是[[阿贝尔群]]（ $\mathbb{Z}$ ， $+$ ）到阿贝尔群 $\left(\mathbb{Z}_{n}, \boldsymbol +\right)$ 的同态。
- 经典的[[同构]]有：
	- logseq.order-list-type:: number
	  $$\ln : \mathbb{R}^{+} \mapsto \mathbb{R}$$
	  是^^正实数乘法群^^到^^实数加法群^^的同构。
	- logseq.order-list-type:: number
	  $$f: \mathbb{Z}_{\phi(n)} \mapsto \mathbb{Z}_{n}\left[\forall z\left(z \in \mathbb{Z}_{\phi(n)} \rightarrow f(z)=g^{z}(\bmod n)\right)\right]$$
	  其中， $g$ 是 $n$ 的[[原根]]。
	  映射 $f$ 是 $\left(\mathbb{Z}_{\phi(n)}, +\right)$ 到 $\left(\mathbb{Z}_{n}, +\right)$ 的同构。