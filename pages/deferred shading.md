public:: false
alias:: 延迟渲染, deferred rendering

- 延迟渲染（Deferred Rendering）是一种渲染技术，特别适用于处理场景中光源数量较多的情况。它与传统的前向渲染（[[Forward Rendering]]）相比，有着根本的不同。
- 在前向渲染过程中，每个场景的几何体需要对每个光源进行计算，这在光源数量较多的情况下会导致性能急剧下降。而延迟渲染技术则采取了不同的方法：首先，它将渲染过程分为两个主要阶段。
	- [[Geometry Pass]]：在这个阶段，引擎渲染场景的所有几何信息到几个不同的2D纹理中，这些纹理集合称为 G 缓冲区（[[G-buffer]]）。这包括**每个像素的位置、颜色、法向量、镜面反射强度、纹理坐标**等信息。
	  logseq.order-list-type:: number
	- [[Lighting Pass]]：在几何传递之后，场景中的光照计算是基于G-buffer中存储的数据进行的。此阶段不直接处理场景的几何形状，而是使用[[G-buffer]]来计算每个像素的光照，独立于场景的复杂性。这使得对每个额外的光源的处理成本变得非常低。
	  logseq.order-list-type:: number
- 延迟渲染的主要优点是其光源处理效率极高，可以处理数百个光源而对性能影响不大。
- 然而，它也有缺点，包括
	- 较高的内存占用（因为需要存储大量的G-buffer数据），
	  logseq.order-list-type:: number
	- 在处理[[透明]]材质方面存在挑战
	  logseq.order-list-type:: number
	- 在[[抗锯齿]]方面存在挑战。
	  logseq.order-list-type:: number
		- [[延迟渲染]]跳过了[[硬件 AA]] 阶段，所以需要用[[FXAA]]这种运行于后处理阶段的算法对生成的图像进行 *AA*.
		  logseq.order-list-type:: number
	- 由于G-buffer的数据结构，延迟渲染通常需要更多的带宽和较强的图形处理能力。
	  logseq.order-list-type:: number
- 此技术广泛应用于游戏和视觉效果行业，尤其是在需要渲染**复杂场景**和**多光源**环境的应用中表现出色。
-
-