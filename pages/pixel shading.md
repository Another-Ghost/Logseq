alias:: pixel shading stage, 像素着色阶段

- #RenderingPipelineStage
- Any per-pixel shading computations are performed here, using the [[interpolated]] [[shading data]] as *input*. 
  The end result is one or more [[colors]] to be passed on to the next stage.
- The [[pixel shading stage]] is executed by *programmable GPU cores*. To that end, the programmer supplies a *program* for the [[pixel shader]] which can contain any desired computations. 
  A large variety of techniques can be employed here, one of the most important of which is [[texturing]]. 
  At its simplest, the end product is a *color value* for each *fragment*, and these are passed on to the next substage.
-
-
-