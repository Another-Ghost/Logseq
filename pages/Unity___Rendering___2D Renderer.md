alias:: 2D Renderer

- ## Sprite Renderer
	- 在 Unity 中，如果你的场景中没有光源，但 Sprite 仍然能够正常渲染，这是因为 Sprite 渲染使用的是一种不同于 3D 模型的渲染方式。
	  collapsed:: true
	  以下是一些关键点解释为什么会出现这种情况：
		- **2D Sprite 渲染**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- Unity 的 2D Sprite 使用的是 `Sprite Renderer` 组件，它是基于屏幕空间渲染的，不依赖于场景中的光源。这意味着 Sprite 的颜色和透明度直接来自于 Sprite 资源的纹理和 `Sprite Renderer` 组件的设置。
		- **默认光照模式**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- 默认情况下，Unity 在 2D 模式下不会应用光照。即使你在场景中添加了光源，只有当你使用了 2D 光照（如 2D 光源组件和 2D 光照材质）时，才会影响 Sprite 的渲染。
		- **材质和着色器**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- Sprite 使用的是 `Sprites/Default` 着色器，该着色器不受光照影响，直接根据纹理的像素颜色进行渲染。除非你更改了 Sprite 的材质和着色器，使其依赖于光照，否则默认情况下不会考虑场景中的光源。
		- **光照设置**：
		  logseq.order-list-type:: number
		  collapsed:: true
			- 如果你的项目需要光照效果，你需要使用 2D 光照系统，比如添加 `2D Renderer` 和 `2D Light` 组件，并配置适当的材质和着色器来支持光照。
			  **总结**：
			  Sprite 的渲染不依赖于光源，是因为它使用的 `Sprite Renderer` 和 `Sprites/Default` 着色器直接根据纹理数据进行渲染，而不受场景中的光照设置影响。这使得 2D 游戏开发更加简单，因为你不需要额外配置光照就能获得预期的视觉效果。只有当你需要特殊的光照效果时，才需要使用 Unity 的 2D 光照系统。
			  <!--Converted by ToLogseq-->
	- 如果在项目中使用 **2D 渲染器（2D Renderer）**，**Universal Render Pipeline Asset **中与 3D 渲染相关的一些选项不会影响最终应用或游戏。
-