alias:: stream output stage

- #RenderingPipelineStage
- The [[stream output stage]] lets us use the *GPU* as a [[geometry engine]]. Instead of sending our processed *vertices* down the rest of the pipeline to be rendered to the screen, at this point we can optionally **output these to an *array* for further processing**. These data can be used by the *CPU*, or the *GPU* itself, in a [[later pass]]. This stage is typically used for [[particle simulations]], such as fireworks.
-