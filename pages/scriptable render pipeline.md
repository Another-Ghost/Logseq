alias:: SRP, 可编程渲染管线

- #UnityRender
- # Definition
	- Unity’s [[Scriptable Render Pipeline]] is a feature that allows you to control rendering via C\# **scripts** .
	  logseq.order-list-type:: number
	- [[SRP]] is the technology that **underpins** the [[Universal Render Pipeline]] and the [[High Definition Render Pipeline]] .
	  id:: 650c2cff-af5a-44c1-bc75-0d2f49760cab
	  logseq.order-list-type:: number
- ## Render Pipeline Instance and Render Pipeline Asset
	- Every [render pipeline]([[Unity/Rendering/RenderPipeline]]) based on [[SRP]] has $2$ key customized elements:
		- A [[render pipeline instance]]. This is an *instance* of a class defines the **functionality** of your [render pipeline]([[Unity render pipeline]]). 
		  logseq.order-list-type:: number
		  Its script inherits from [[Unity/Rendering/RenderPipeline]], and overrides its `Render()` method.
		- A [[Unity/Rendering/Render Pipeline Asset]]. This is an *asset* in your Unity Project that stores data about **which [[Render Pipeline Instance]] to use, and how to configure it**. Its script inherits from [[RenderPipelineAsset]] and overrides its `CreatePipeline()` method.
		  logseq.order-list-type:: number
- ## ScriptableRenderContext
	- [[ScriptableRenderContext]] is a class that acts as an *interface* between the custom C# code in the [render pipeline]([[Unity/Rendering/RenderPipeline]]) and Unity’s [[low-level graphics]] code .
- ## Entry points and callbacks
	- [RenderPipeline.Render](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.RenderPipeline.Render.html) is the main entry point to the SRP. Unity calls this method automatically.
	- The [[RenderPipelineManager]]class has the following events that you can subscribe to, so that you can execute custom code at specific points in the [[render loop]]:
		- [beginContextRendering](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.RenderPipelineManager-beginContextRendering.html)
		  logseq.order-list-type:: number
		- [endContextRendering](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.RenderPipelineManager-endContextRendering.html)
		  logseq.order-list-type:: number
		- [beginCameraRendering](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.RenderPipelineManager-beginCameraRendering.html)
		  logseq.order-list-type:: number
		- [endCameraRendering](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.RenderPipelineManager-endCameraRendering.html)
		  logseq.order-list-type:: number
		-