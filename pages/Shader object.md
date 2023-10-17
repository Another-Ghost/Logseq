alias:: Shader objects

- #UnityRender
- an [[instance]] of the [[shader class]].
- A [[Shader object]] is a *wrapper* for [[shader programs]] and *instructions* for changing settings on the GPU (collectively called the [[render state]]), and information that tells Unity how to use them.
- A Shader object has a nested structure. It organizes *information* into structures called [[SubShaders]] and [[Passes]]. It organizes *shader programs* into [[shader variants]].
- ## Defining a Shader object
	- Inside the `Shader` block, you can:
		- Define [[material properties]], using the `Properties` block. See [ShaderLab: defining material properties](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-Properties.html).
		  logseq.order-list-type:: number
		- Define one or more [[SubShaders]], using the `SubShader` block. See [ShaderLab: defining a SubShader](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-SubShader.html).
		  logseq.order-list-type:: number
		- Assign a [custom editor](https://docs.unity3d.com/2023.2/Documentation/Manual/editor-CustomEditors.html), which determines how the shader asset appears in the Unity Editor. Optionally, you can assign different custom editors for different render pipelines. See [ShaderLab: assigning custom editors](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-CustomEditor.html).
		  logseq.order-list-type:: number
		- Assign a [[fallback Shader object]], using the `Fallback` block. See [ShaderLab: assigning a fallback](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-Fallback.html).
		  logseq.order-list-type:: number
- `Shader "<name>"`
  `{`
      `<optional: Material properties>`
      `<One or more SubShader definitions>`
      `<optional: custom editor>`
      `<optional: fallback>`
  `}`
-