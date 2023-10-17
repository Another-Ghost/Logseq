alias:: viewport matrix

- 设[[window]]是 $n_x\times n_y$ [[像素]]的, 则把[[NDC]]转换到 [[window coordinates]]的[[viewport tranformation]]可表示为：
  $$
  \begin{bmatrix}x_\text{screen}\\y_\text{screen}\\1\end{bmatrix}=\begin{bmatrix}\frac{n_x}2&0&\frac{n_x-1}2\\0&\frac{n_y}2&\frac{n_y-1}2\\0&0&1\end{bmatrix}\begin{bmatrix}x_\text{canonical}\\y_\text{canonical}\\1\end{bmatrix}
  $$
- $z$ 轴作为[[投影方向]], $z$坐标依旧保持区间为$[-1,1]$, 在计算[[深度]]时会用到。
  完整的[[齐次坐标]]下的[[viewport matrix]]为：
  $$
  M_{\text{viewport}}=\begin{bmatrix}\frac{n_x}{2}&0&0&\frac{n_x-1}{2}\\0&\frac{n_y}{2}&0&\frac{n_y-1}{2}\\0&0&1&0\\0&0&0&1\end{bmatrix}
  $$
-