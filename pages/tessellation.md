alias:: tessellation stage

- #RenderingPipelineStage
- With tessellation, a [[curved surface]] can be generated with an **appropriate number** of *triangles*.
- *Vertices* can be used to describe *points*, *lines*, *triangles*, or other *objects*, but also [[curved surface]], such as a *ball*. Such surfaces can be specified by a *set of [[patches]]*, and each [[patch]] is made of a set of *vertices*. 
  The [[tessellation stage]] consists of a series of stages itself—[[hull shader]], [[tessellator]], and [[domain shader]]—that converts these *sets of patch vertices* into (normally) **larger** *sets of vertices* that are then used to make new *sets of triangles*. 
  The [[camera]] for the *scene* can be used to **determine how many *triangles* are generated**: many when the patch is close, few when it is far away.