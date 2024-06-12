alias:: RenderPipelineAsset, Render Pipeline Asset

- 在 Unity 中，Render Pipeline Asset 和 Renderer 之间有着紧密的关系，它们共同决定了渲染管线的行为和性能。以下是二者关系的详细解释：
- ### Render Pipeline Asset
  **Render Pipeline Asset** 是一个全局的配置文件，用于定义渲染管线的各种全局设置和参数。它是渲染管线的入口点，决定了整个渲染流程的基础配置。
	- **作用**：Render Pipeline Asset 配置了渲染管线的核心属性，如通用设置、质量设置和特效设置。
	- **类型**：根据使用的渲染管线，Render Pipeline Asset 可以是 Universal Render Pipeline Asset (URP Asset) 或 High Definition Render Pipeline Asset (HDRP Asset) 等。
	- **位置**：它通常在项目设置中被指定为当前项目的渲染管线。
- ### [Renderer]([[Unity/Rendering/Renderer]])
  **Renderer** 是具体执行渲染逻辑的组件或类。它定义了如何渲染场景中的对象、如何应用后处理效果等。Renderer 是在 Render Pipeline Asset 中配置和管理的。
	- **作用**：Renderer 负责具体的渲染操作，包括渲染顺序、光照、阴影和后处理效果等。
	- **类型**：根据渲染管线的不同，Renderer 可以是 Universal Renderer (用于 URP) 或 HD Renderer (用于 HDRP) 等。
	- **配置**：Renderer 的配置是通过 Renderer Asset 完成的，这些资产被分配到 Render Pipeline Asset 中以定义不同的渲染行为。
- ### 二者关系
	- **组合关系**：
	  logseq.order-list-type:: number
		- Render Pipeline Asset 包含一个或多个 Renderer Asset。这些 Renderer Asset 定义了具体的渲染行为和设置。
		- 在 Unity 中，当你创建一个 URP Asset 或 HDRP Asset 时，你需要指定一个默认的 Renderer。这个 Renderer 定义了如何处理渲染任务。
	- **配置和管理**：
	  logseq.order-list-type:: number
		- 你可以在 Render Pipeline Asset 中配置多个 Renderer，并在不同的场景或需要时切换使用不同的 Renderer。
		- 通过这种方式，你可以在同一个项目中灵活地应用不同的渲染策略，以适应不同的需求（例如不同的质量设置、平台要求等）。
	- **示例**：
	  logseq.order-list-type:: number
		- **URP**：创建一个 URP Asset 并配置一个 Forward Renderer。Forward Renderer 定义了所有前向渲染的设置和行为，如光照模式、阴影、后处理等。
		- **HDRP**：创建一个 HDRP Asset，并配置一个 HD Renderer。HD Renderer 定义了高级光照模型、反射、体积光照和其他高质量渲染特效。
- ### 配置步骤
	- **创建 Render Pipeline Asset**：
	  logseq.order-list-type:: number
		- 右键点击 `Assets` 文件夹，选择 `Create > Rendering > Universal Render Pipeline > Pipeline Asset`（或 HDRP）。
	- **创建 Renderer Asset**：
	  logseq.order-list-type:: number
		- 对于 URP，右键点击 `Assets` 文件夹，选择 `Create > Rendering > Universal Render Pipeline > Forward Renderer`。
		- 对于 HDRP，这通常包含在 HDRP Asset 的配置中，或者你可以自定义渲染器。
	- **配置 Render Pipeline Asset**：
	  logseq.order-list-type:: number
		- 选择创建的 Render Pipeline Asset，在 `Inspector` 面板中找到 `Renderer List`，将创建的 Renderer Asset 添加到列表中。
		- 在项目设置中（`Edit > Project Settings`），将 `Graphics` 部分的 `Scriptable Render Pipeline Settings` 设置为你的 Render Pipeline Asset。
- ### 总结
	- **Render Pipeline Asset** 决定了渲染管线的全局设置和配置，是渲染流程的入口点。
	- **Renderer** 决定了具体的渲染逻辑和效果，是实际执行渲染的核心组件。
	- **Render Pipeline Asset 包含并管理 Renderer**，使得你可以通过不同的 Renderer 来实现灵活的渲染策略。
	  通过这种组合和配置方式，Unity 能够提供高度可定制和高效的渲染解决方案，以满足各种游戏和应用的需求。
	  <!--Converted by ToLogseq-->