alias:: application stage, 应用程序阶段

- the [[application stage]] is **driven by the application** and is therefore typically implemented in software running on *general-purpose* [[CPUs]]. 
  Some of the tasks traditionally performed on the *CPU* include [[collision detection]], [[global acceleration algorithms]], [[animation]], [[physics simulation]], and many others, depending on the type of application. 
  An *application stage algorithm* or *setting* could decrease the number of triangles to be rendered.
- > Some *application* work can be performed by the [[GPU]], using a *separate
  mode* called a [[compute shader]].
- At the end of the *application stage*, the *geometry to be rendered* is fed to the [[geometry processing stage]]. These are the [[rendering primitives]].
  This is the **most important task** of the *application stage*.