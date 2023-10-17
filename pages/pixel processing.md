alias:: pixel processing stage, 像素处理阶段, per-pixel processing

- #RenderingPipelineStage
- The [[pixel processing stage]] executes a *program* **per** [[pixel]] to determine its [[color]] and may perform [[depth testing]] to see whether it is *visible* or not. 
  It may also perform *per-pixel operations* such as [[blend]].
  It is processed entirely on the [[GPU]].
- The [[pixel processing stage]] is divided into [[pixel shading]] and [[merging]].