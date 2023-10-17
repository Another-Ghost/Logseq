- Here is where each *pixel* that has its *center* covered by the *triangle* is checked and a [[fragment]] generated for **the part of the pixel that overlaps the triangle**. 
  id:: 64d81c68-28e7-452a-9324-dc553f92fedc
- Finding which *samples* or *pixels* are **inside** a *triangle* is often called [[triangle traversal]]. 
  Each *triangle fragment*’s properties are generated using data [[interpolated]] among the $3$ *triangle vertices*. These properties include the fragment’s [[depth]], as well as any [[shading data]] from the geometry stage.
- All *pixels* or *samples* that are inside a *primitive* are then sent to the [[pixel processing stage]].
-