alias:: 内积空间, 预希尔伯特空间

- ### 定义
  内积空间是一个向量空间，配备了一个额外的结构，即内积。内积是一个将两个向量映射到标量的函数，通常表示为 \(\langle u, v \rangle\)，其中 \(u\) 和 \(v\) 是向量空间中的元素。这个内积满足以下性质：
  1. **共轭对称性**：\(\langle u, v \rangle = \overline{\langle v, u \rangle}\)。
  2. **线性**：对任意标量 \(\alpha\) 和 \(\beta\)，有 \(\langle \alpha u + \beta v, w \rangle = \alpha\langle u, w \rangle + \beta\langle v, w \rangle\)。
  3. **正定性**：\(\langle u, u \rangle \geq 0\)，且 \(\langle u, u \rangle = 0\) 当且仅当 \(u = 0\)。
- ### 例子
  
  **实数向量空间**：在 \(\mathbb{R}^n\) 中，内积可以定义为两个向量的点积，即 \(\langle u, v \rangle = u_1v_1 + u_2v_2 + \cdots + u_nv_n\)。
  
  **复数向量空间**：在 \(\mathbb{C}^n\) 中，内积是 \(\langle u, v \rangle = u_1\overline{v_1} + u_2\overline{v_2} + \cdots + u_n\overline{v_n}\)，其中 \(\overline{v_i}\) 表示 \(v_i\) 的复共轭。
- ### 应用
  
  内积空间提供了衡量向量长度（范数）和夹角的方法。特别是，向量 \(u\) 的范数定义为 \(\|u\| = \sqrt{\langle u, u \rangle}\)。两个向量的夹角 \(\theta\) 通过余弦定理和内积关联，即 \(\cos\theta = \frac{\langle u, v \rangle}{\|u\|\|v\|}\)。
- ### 扩展
  
  内积空间可以进一步扩展到希尔伯特空间（Hilbert Space），这是完备的内积空间，即任何柯西序列都在该空间中收敛。希尔伯特空间在量子力学和泛函分析中扮演着核心角色。
- ## [[实内积空间]]
-