alias:: z-buffer, 深度缓存, z缓冲

- A [[z-buffer]] is the **same size and shape** as the [[color buffer]], and for each *pixel* it stores the [[z-value]] to the **currently closest primitive**. 
  The *z-buffer* algorithm is simple, has $O(n)$ *convergence* (where $n$ is the number of *primitives* being rendered). 
  Also note that this algorithm allows most primitives to be rendered in any order, which is another reason for its popularity. 
  However, the *z-buffer* stores only a single *depth* at each point on the screen, so it cannot be used for partially [[transparent]] primitives. These must be rendered after all [[opaque]] primitives, and in *back-to-front order*, or using a separate *order-independent algorithm*. 
  [[Transparency]] is one of the **major weaknesses** of the basic [[z-buffer]].
- There are other [[channels]] and [[buffers]] that can be used to [[filter]] and *capture* *fragment information*. 
  The [[alpha channel]] is associated with the [[color buffer]] and stores a related [[opacity]] value for each pixel.
  >In older APIs, the alpha channel was also used to *discard* pixels selectively via the *alpha test* feature. Nowadays a *discard* operation can be inserted into the *pixel shader* program and any type of computation can be used to trigger a discard. 
  This type of test can be used to ensure that [[fully transparent]] *fragments* do not affect the [[z-buffer]].