alias:: projection matrix

- #RenderingPipelineStage
- As part of [[vertex shading]], *rendering systems* perform [projection]([[projection stage]]) and then [[clipping]], which [[transforms]] the [[view volume]] into a [[unit cube]] with its [[extreme points]] at $(−1, −1, −1)$ and $(1, 1, 1)$.
  >Different *ranges* defining the same [[volume]] can and are used, for example, $0 ≤ z ≤ 1$.
- The *unit cube* is called the [[canonical view volume]].
  [Projection]([[projection stage]]) is done first, and on the *GPU* it is done by the [[vertex shader]]. There are two commonly used *projection methods*, namely [[orthographic projection]] and [[perspective projection]].
- After either *transform*, the *models* are said to be in [[clip coordinates]]. These are in fact [[homogeneous coordinates]] and so this occurs before *division* by $w$.
- The *GPU’s vertex shader* must always output *coordinates* of this type in order for the next functional stage, [[clipping]], to work correctly.
- Although these [[matrices]] transform* one [[volume]] into another, they are called [[projections]] because after display, the *z-coordinate* is not stored in the image generated but is stored in a [[z-buffer]]. 
  In this way, the *models* are *projected* from *three* to *two* [[dimensions]].
-