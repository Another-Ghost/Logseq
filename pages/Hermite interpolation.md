alias:: Hermite 插值, 埃尔米特插值

- ## 定义
	- 考虑一组数据点 \(\{(x_i, y_i, y'_i)\}_{i=0}^n\)，其中 \(x_i\) 是插值节点，\(y_i\) 是函数 \(f\) 在 \(x_i\) 处的值，\(y'_i\) 是 \(f\) 在 \(x_i\) 处的一阶导数。赫米特插值问题是寻找一个多项式 \(H(x)\)，满足以下条件：
	  
	  $$ H(x_i) = y_i, \quad H'(x_i) = y'_i, \quad \text{for } i = 0, 1, \ldots, n $$
	- ### 插值多项式的构造
	  赫米特插值多项式 \(H(x)\) 可以表示为：
	  $$ H(x) = \sum_{i=0}^{n} [y_i h_{2i}(x) + y'_i h_{2i+1}(x)] $$
	  其中，\(h_{2i}(x)\) 和 \(h_{2i+1}(x)\) 是[[赫米特插值基函数]]，它们构造于[[拉格朗日插值基函数]]，满足：
	  $$ h_{2i}(x_j) = \delta_{ij}, \quad h_{2i}'(x_j) = 0, \quad h_{2i+1}(x_j) = 0, \quad h_{2i+1}'(x_j) = \delta_{ij} $$
	  这里，\(\delta_{ij}\) 是[[克罗内克δ函数]]。
	- ### [[赫米特插值基函数]]
	  赫米特插值基函数 \(h_{2i}(x)\) 和 \(h_{2i+1}(x)\) 通过组合拉格朗日插值基函数 \(L_{i}(x)\) 构造。对于 \(n+1\) 个节点的拉格朗日基函数 \(L_{i}(x)\) 定义为：
	  $$ L_{i}(x) = \prod_{\substack{0 \leq j \leq n \\ j \neq i}} \frac{x - x_j}{x_i - x_j} $$
	  那么，赫米特插值基函数可进一步定义为：
	  $$ h_{2i}(x) = (1 - 2L'_{i}(x_i)(x - x_i))L_{i}^2(x), \quad h_{2i+1}(x) = (x - x_i)L_{i}^2(x) $$
- ### 基本原理
  假设给定一组数据点 \((x_0, y_0), (x_1, y_1), \ldots, (x_n, y_n)\)，以及这些点处函数的导数值 \(y'_0, y'_1, \ldots, y'_n\)。赫米特插值的目标是找到一个多项式 \(H(x)\)，使得在每个数据点 \(x_i\) 上，\(H(x_i) = y_i\) 且 \(H'(x_i) = y'_i\)。
- ### 插值多项式的构造
  赫米特插值多项式通常采用以下形式：
  \[ H(x) = \sum_{i=0}^{n} [y_i h_{2i}(x) + y'_i h_{2i+1}(x)] \]
  其中，\(h_{2i}(x)\) 和 \(h_{2i+1}(x)\) 是基于赫米特插值基函数构造的。这些基函数保证了在每个插值点上，多项式不仅匹配函数值，还匹配导数值。
- ### 赫米特插值基函数
  赫米特插值基函数是特殊设计的多项式，用于确保赫米特插值的条件得到满足。对于第 \(i\) 个数据点 \(x_i\)，基函数 \(h_{2i}(x)\) 和 \(h_{2i+1}(x)\) 分别用于确保 \(H(x_i) = y_i\) 和 \(H'(x_i) = y'_i\)。这些基函数通常通过组合拉格朗日插值基函数来构造。
- ### 特点和应用
	- **高精度**：赫米特插值通过考虑函数在插值点的导数，提供了比普通[[拉格朗日插值]]或[[牛顿插值]]更高的精度。
	- **平滑性**：在处理[[曲线拟合]]和[[曲面拟合]]时，赫米特插值可以产生更平滑的曲线，因为它考虑了斜率信息。
	- **应用领域**：赫米特插值在计算机图形学、动画、数值分析中尤其有用，用于生成平滑曲线和曲面。
	  id:: 658d9b57-3874-44e9-a5ab-6c09f5ae3597
	- 需要注意的是，赫米特插值多项式的构造比较复杂，尤其是当插值点数量较多时。此外，与其他高阶插值方法一样，赫米特插值可能会遇到[[龙格现象]]。