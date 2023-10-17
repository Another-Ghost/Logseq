alias:: 渲染路径, rendering paths

- #UnityRender
- Unity’s [[Built-In Render Pipeline]] supports different [[rendering paths]].
- A [[rendering path]] is a series of operations related to [[lighting]] and [[shading]].
- Different *rendering paths* have different capabilities and performance characteristics. Deciding on which rendering path is most suitable for your Project depends on the type of Project, and on the target hardware.
- You can choose the rendering path that your Project uses in the [Graphics](https://docs.unity3d.com/2023.2/Documentation/Manual/class-GraphicsSettings.html) window, and you can override that path for each [[camera]].
- If the GPU on the device running your Project does not support the rendering path that you have selected, Unity automatically uses a lower fidelity rendering path. 
  >For example, on a GPU that does not handle **Deferred Shading**[](https://docs.unity3d.com/2023.2/Documentation/Manual/RenderTech-DeferredShading.html)**[](https://docs.unity3d.com/2023.2/Documentation/Manual/Glossary.html#Deferredshading)**, Unity uses **Forward Rendering**[](https://docs.unity3d.com/2023.2/Documentation/Manual/RenderTech-ForwardRendering.html)**[](https://docs.unity3d.com/2023.2/Documentation/Manual/Glossary.html#ForwardRendering)**.
-
-