alias:: SubShaders

- [[SubShaders]] let you separate your [[Shader object]] into parts that are compatible with different [[hardware]], [[render pipelines]], and [[runtime settings]].
- ## Using the SubShader block
	- In ShaderLab, you define a SubShader by placing a `SubShader` [[block]] inside a `Shader` [[block]].
	- Inside the `SubShader` block, you can:
		- Assign a [[LOD]][](https://docs.unity3d.com/2023.2/Documentation/Manual/LevelOfDetail.html)
		  logseq.order-list-type:: number
		  **[](https://docs.unity3d.com/2023.2/Documentation/Manual/Glossary.html#LOD)** (level of detail) value to the SubShader, using the `LOD` block. See [assigning a LOD value to a SubShader](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-ShaderLOD.html).
		- Assign key-value pairs of data to the SubShader, using the `Tags` block. See [ShaderLab: assigning tags to a SubShader](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-SubShaderTags.html).
		  logseq.order-list-type:: number
		- Add GPU instructions or shader code to the SubShader, using [[ShaderLab commands]]. See [ShaderLab: using commands](https://docs.unity3d.com/2023.2/Documentation/Manual/shader-shaderlab-commands.html).
		  logseq.order-list-type:: number
		- Define one or more [[Passes]], using the `Pass` block. See [ShaderLab: defining a Pass](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-Pass.html).
		  logseq.order-list-type:: number
		- Specify package requirements using the `PackageRequirements` block. This makes Unity only run the SubShader if the required packages are installed. See [ShaderLab: specifying package requirements](https://docs.unity3d.com/2023.2/Documentation/Manual/SL-PackageRequirements.html).
		  logseq.order-list-type:: number
	- `SubShader`
	  `{`
	      `<optional: LOD>`
	      `<optional: tags>`
	      `<optional: commands>`
	      `<One or more Pass definitions>`
	  `}`
-