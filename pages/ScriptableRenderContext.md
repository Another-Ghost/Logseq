- >Use the [ScriptableRenderContext](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.ScriptableRenderContext.html) API to schedule and execute rendering commands. For information, see [Scheduling and executing rendering commands in the Scriptable Render Pipeline](https://docs.unity3d.com/2023.2/Documentation/Manual/srp-using-scriptable-render-context.html).
- you use the ScriptableRenderContext to build up a **list of [[rendering commands]]**, and then you tell Unity to execute them. Unity’s [[low-level graphics]] architecture then sends *instructions* to the [[graphics API]].
- To schedule rendering commands, you can:
	- Pass [[CommandBuffers]] to the [[ScriptableRenderContext]], using [ScriptableRenderContext.ExecuteCommandBuffer](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.ScriptableRenderContext.ExecuteCommandBuffer.html)
	  logseq.order-list-type:: number
	- Make **direct API calls** to the [[Scriptable Render Context]], such as [ScriptableRenderContext.Cull](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.ScriptableRenderContext.Cull.html) or [ScriptableRenderContext.DrawRenderers](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.ScriptableRenderContext.DrawRenderers.html)
	  logseq.order-list-type:: number
- To tell Unity to perform the commands that you have scheduled, call [ScriptableRenderContext.Submit](https://docs.unity3d.com/2023.2/Documentation/ScriptReference/Rendering.ScriptableRenderContext.Submit.html).
	- Unity schedules all rendering commands on the ScriptableRenderContext in the same way, and does **not execute any of them until** you call `Submit()`.
-