alias:: 窗函数

- 在设计FIR低通滤波器时，选择合适的窗函数对于确定冲激响应的形状和滤波器的频率特性至关重要。以下是一些常用的窗函数及其特性：
- ### 矩形窗 (Rectangular Window)
  logseq.order-list-type:: number
  矩形窗是最简单的窗函数，其表达式为：
  $$
  w(n) = R_N(n) = \left\{
  \begin{array}{ll}
  1, & 0 \leq n \leq N-1 \\
  0, & \text{otherwise}
  \end{array}
  \right.
  $$
  矩形窗在[[主瓣]]宽度最小的同时，具有最大的[[旁瓣]]高度，导致滤波器的频率选择性不是很好。
- ### 三角窗 (Triangular Window)
  logseq.order-list-type:: number
  三角窗，或称为巴特利特窗，其表达式为线性递减形式：
  $$
  w(n) = 1 - \left| \frac{2n - (N-1)}{N-1} \right|, \quad 0 \leq n \leq N-1=
  $$
  这个窗函数在时间域内形成一个三角形状，旁瓣比矩形窗低，但主瓣宽度更宽。
- ### 汉宁窗 (Hanning Window)
  logseq.order-list-type:: number
  汉宁窗提供了更平滑的过渡，其表达式为：
  \begin{aligned}
  w(n) &= 0.5\left[1 - \cos\left(\frac{2 \pi n}{N-1}\right)\right] R_N(n), \quad 0 \leq n \leq N-1 \\
  &= \left\{\begin{array}{cl}
  \frac{2 n}{N-1} ; & 0 \leq n \leq \frac{1}{2}(N-1) \\
  2-\frac{2 n}{N-1} ; & \frac{1}{2}(N-1) \leq n \leq N-1
  \end{array}\right.
  \end{aligned}
  汉宁窗的旁瓣比矩形窗和三角窗低，适合于频率选择性要求较高的应用。
- ### 哈明窗 (Hamming Window)
  logseq.order-list-type:: number
  汉明窗类似于汉宁窗，但有稍微不同的系数，提供更小的旁瓣：
  $$
  w(n) = \left[0.54 - 0.46 \cos\left(\frac{2 \pi n}{N-1}\right)\right] R_N(n), \quad 0 \leq n \leq N-1
  $$
  汉明窗的旁瓣衰减速度比汉宁窗更快，使其在许多应用中更受欢迎。
- ### 布莱克曼窗 (Blackman Window)
  logseq.order-list-type:: number
  布莱克曼窗在减少旁瓣高度方面表现出色，其表达式为：
  $$
  w(n) = \left[0.42 - 0.5 \cos\left(\frac{2 \pi n}{N-1}\right) + 0.08 \cos\left(\frac{4 \pi n}{N-1}\right)\right] R_N(n), \quad 0 \leq n \leq N-1
  $$
  布莱克曼窗的主瓣较宽，但其旁瓣远小于汉明窗和汉宁窗，非常适用于需要严格旁瓣抑制的应用场合。
- ### [[凯塞窗]]
  logseq.order-list-type:: number
- 每种窗函数都有其独特的特性，设计者根据具体的应用需求选择合适的窗函数来设计FIR滤波器。例如，如果应用中旁瓣的抑制是首要考虑的，布莱克曼窗或汉明窗可能是较好的选择；如果主要考虑主瓣宽度，则可能选择矩形窗或三角窗。
  <!--Converted by ToLogseq-->