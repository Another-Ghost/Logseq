alias:: Passes

- A Pass is the **fundamental element** of a Shader object. It contains instructions for setting the state of the GPU, and the shader programs that run on the GPU.
- Simple Shader objects might contain only a single Pass, but more complex shaders can contain multiple Passes. You can **use separate Passes to define parts of your Shader object that work differently**; for example, parts that require a change to the render state, different shader programs, or a different `LightMode` Pass tag.
	- > In render pipelines based on the Scriptable [**Render Pipeline**](https://docs.unity3d.com/2023.2/Documentation/Manual/render-pipelines.html)
	  **[](https://docs.unity3d.com/2023.2/Documentation/Manual/Glossary.html#Renderpipeline)**, you can use a [[RenderStateBlock]] to change the render state on the GPU, without requiring a separate Pass.
- ## Using the Pass block
	- To define a regular Pass in ShaderLab, you place a `Pass` block inside a `SubShader` block.
	- Inside the `Pass` block, you can:
		- Assign a name to the Pass, using a Name block. See [ShaderLab: assigning a name to a Pass](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-Name.html).
		  logseq.order-list-type:: number
		- Assign key-value pairs of data to the Pass, using a Tags block. See [ShaderLab: assigning tags to a Pass](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-PassTags.html).
		  logseq.order-list-type:: number
		- Perform operations using [[ShaderLab commands]]. See [ShaderLab: using commands](https://docs.unity3d.com/2023.2/Documentation/Manual/shader-shaderlab-commands.html).
		  logseq.order-list-type:: number
		- Add [[shader code]] to the Pass, using a [[shader code block]]. See [ShaderLab: shader code blocks](https://docs.unity3d.com/2023.2/Documentation/Manual/shader-shaderlab-code-blocks.html).
		  logseq.order-list-type:: number
		- Specify package requirements using the `PackageRequirements` block. This makes Unity only run the Pass if the required packages are installed. See [ShaderLab: specifying package requirements](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-PackageRequirements.html).
		  logseq.order-list-type:: number
	- You can also define two special types of Pass, using the `UsePass` or `GrabPass` commands. For information on those commands, see [ShaderLab commands: UsePass](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-UsePass.html) or [ShaderLab commands: GrabPass](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-GrabPass.html).