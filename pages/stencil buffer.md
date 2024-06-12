alias:: 模板缓存, 模板缓冲

- 模板缓冲区 (Stencil Buffer) 是一个非常强大的工具，用于在渲染过程中进行复杂的像素操作和效果。它允许你对每个像素进行条件性写入和测试，从而实现诸如遮罩、镜像、轮廓描边等效果。
- ### Stencil Buffer 的基本概念
	- **模板缓冲区的大小**：
	  通常，模板缓冲区是一个 8 位的缓冲区，这意味着每个像素有 256 种可能的模板值。
	- **模板测试 (Stencil Test)**：
	  在渲染过程中，模板测试决定了当前像素是否通过模板缓冲区的条件，从而决定是否绘制该像素。
	- **模板操作 (Stencil Operation)**：
	  这是在模板测试通过或失败后对模板缓冲区进行的操作，如增加、减少、保留等。
- ### Unity 中的 Stencil Buffer 使用
- 在 Unity 中，你可以通过自定义的 Shader 和渲染设置来使用模板缓冲区。以下是一个简单的示例，展示如何在 Shader 中使用模板缓冲区：
- #### 示例 Shader
  ```csharp
  Shader "Custom/StencilExample"
  {
    SubShader
    {
        Tags { "RenderType" = "Opaque" }
  
        Pass
        {
            // 模板缓冲设置
            Stencil
            {
                Ref 1              // 模板参考值
                Comp equal         // 比较函数：是否等于参考值
                Pass replace       // 如果通过模板测试，替换当前模板值
                Fail keep          // 如果模板测试失败，保持当前模板值
                ZFail keep         // 如果深度测试失败，保持当前模板值
            }
  
            CGPROGRAM
            #pragma vertex vert
            #pragma fragment frag
  
            // 你的着色器代码...
  
            ENDCG
        }
    }
  }
  ```
- ### 模板缓冲区设置详解
	- **Ref**:
	  模板参考值。在进行模板测试时，会将这个值与模板缓冲区中的当前值进行比较。
	- **Comp**:
	  模板比较函数，定义了如何比较模板缓冲区中的当前值和参考值。常用的比较函数包括：
		- `always`：总是通过模板测试。
		- `never`：从不通过模板测试。
		- `less`：当当前值小于参考值时通过。
		- `equal`：当当前值等于参考值时通过。
		- `greater`：当当前值大于参考值时通过。
		- `notEqual`：当当前值不等于参考值时通过。
		- `lessEqual`：当当前值小于等于参考值时通过。
		- `greaterEqual`：当当前值大于等于参考值时通过。
	- **Pass**:
	  当模板测试通过时对模板缓冲区进行的操作。常用操作包括：
		- `keep`：保持当前值不变。
		- `zero`：将模板值设置为 0。
		- `replace`：用参考值替换当前模板值。
		- `incrSat`：将模板值加 1，若超出 255 则保持 255。
		- `decrSat`：将模板值减 1，若小于 0 则保持 0。
		- `invert`：按位取反当前模板值。
	- **Fail**:
	  当模板测试失败时对模板缓冲区进行的操作。
	- **ZFail**:
	  当深度测试失败时对模板缓冲区进行的操作。
- ### 示例场景：创建遮罩效果
	- **设置遮罩区域**：
	  logseq.order-list-type:: number
	  使用一个物体设置模板缓冲区的值，定义一个遮罩区域。```csharp
	  Shader "Custom/StencilMask"
	  {
	     SubShader
	     {
	         Tags { "RenderType" = "Opaque" }
	         Pass
	         {
	             Stencil
	             {
	                 Ref 1
	                 Comp always
	                 Pass replace
	                 Fail keep
	                 ZFail keep
	             }
	             // 不需要渲染任何东西，只修改模板缓冲区
	             ColorMask 0
	         }
	     }
	  }
	  ```
	  - **应用遮罩效果**：
	  logseq.order-list-type:: number
	  仅在模板缓冲区值等于 1 的区域内进行渲染。```csharp
	  Shader "Custom/StencilApply"
	  {
	     SubShader
	     {
	         Tags { "RenderType" = "Opaque" }
	         Pass
	         {
	             Stencil
	             {
	                 Ref 1
	                 Comp equal
	                 Pass keep
	                 Fail keep
	                 ZFail keep
	             }
	             // 你的实际渲染代码
	             CGPROGRAM
	             #pragma vertex vert
	             #pragma fragment frag
	  
	             // 你的着色器代码...
	  
	             ENDCG
	         }
	     }
	  }
	  ```
- 通过使用模板缓冲区，你可以实现复杂的渲染效果，并精确控制渲染过程中的每个像素。模板缓冲区的强大之处在于其灵活性，可以用于许多高级渲染技术，如多重通过、轮廓描边、镜像反射等。
  <!--Converted by ToLogseq-->