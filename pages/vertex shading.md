alias:: 顶点着色

- #RenderingPipelineStage
- ### Two Tasks of Vertex Shading
	- There are two main tasks of [[vertex shading]], namely,  to **compute the [[position]] for a vertex** and to **evaluate whatever the programmer may like to have as [[vertex output data]]**, such as a [[normal]] and [[texture coordinates]].
- ### Origin of the Name of Vertex Shader
	- **Traditionally** much of the *shade* of an object was computed by applying [[lights]] to each *vertex’s location* and *normal* and *storing* only the *resulting [[color]] at the [[vertex]]. 
	  These colors were then [[interpolated]] across the [[triangle]]. 
	  **For this reason**, this *programmable vertex processing unit* was named the [[vertex shader]].
	  **With the advent** of the modern *GPU*, along with some or all of the shading taking place per pixel, this vertex shading stage is more general and may not evaluate any shading equations at all. 
	  The vertex shader is now a more general unit dedicated to **setting up the data associated with each [[vertex]]**. As an example, the vertex shader can [[animate]] an object.
- ### Coordinate System
	- We start by describing how the *vertex position* is computed, a *set* of *coordinates*
	  that is always required. On its way to the screen, a model is [[transformed]] into several different [[coordinate systems]].
	- It is possible to have several [[model transforms]] associated with a single model. This allows several copies (called [[instances]]) of the same model to have different [[locations]], [[orientations]], and [[sizes]] in the same [[scene]].
- ### Model Transform and World Space
	- It is the [[vertices]] and the [[normals]] of the *model* that are **transformed** by the [[model transform]]. The *coordinates* of an object are called [[model coordinates]],
	- and after the [[model transform]] has been applied to these coordinates, the model is said to be located in [[world space]].
	- > The *world space* is **unique**, and after the models have been transformed with their respective *model transforms*, all models exist in this **same** *space*.
- ### View Transform and View Space
	- Only the *models* that the [[camera]] sees are *rendered*. 
	  To facilitate [projection]([[projection stage]]) and [[clipping]], the *camera* and all the *models* are *transformed* with the [[view transform]]. 
	  The purpose of the [[view transform]] is to **place the *camera* at the [[origin]]** and aim it, to make it **look in the direction of the [[negative z-axis]]**, with the **[[y-axis]] pointing [[upward]]** and the **[[x-axis]] pointing to the [[right]]**.
	- The *space* thus delineated is called [[view space]].
- ### The Second Type of Output from Vertex Shading
	- To produce a realistic scene, it is not sufficient to render the shape and position of objects, but their appearance must be modeled as well. 
	  This description includes each object’s material, as well as the effect of any light sources shining on the object. 
	  The operation of determining the effect of a [[light]] on a [[material]] is known as [[shading]] .
	  It involves computing a [[shading equation]] at various points on the object. Typically, some of these computations are performed during [[geometry processing]] on a [[model]]’s [[vertices]], and others may be performed during [[per-pixel processing]]. 
	  A variety of *material data* can be *stored* at each *vertex*, such as the point’s *location*, a *normal*, a *color*, or any other *numerical information* that is needed to evaluate the [[shading equation]].
- ### Vertex Shading Results
	- [[Vertex shading results]] are then sent to the [[rasterization]] and [[pixel processing stages]] to be [[interpolated]] and used to compute the [[shading of the surface]].
- ### [Projection]([[projection stage]])
- ### Optional Vertex Processing
	- Every *pipeline* has the *vertex processing* just described. Once this processing is done, there are a few *optional stages* that can take place on the *GPU*, in this **order**: [[tessellation]], [[geometry shading]], and [[stream output]].
	- Their use depends both on the capabilities of the *hardware*—* *not all** *GPUs* have them—and the desires of the programmer. They are *independent* of each other, and in general they are not commonly used.
	- Regardless of which (if any) optional stages are used, if we continue down the *pipeline* we have a set of *vertices* with [[homogeneous coordinates]] that will be checked for whether the *camera* views them.