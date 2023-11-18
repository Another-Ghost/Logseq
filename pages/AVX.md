alias:: Advanced Vector Extension, 高级向量扩展

- AVX 浮点体系结构允许数据存储在
  16 个 YMM 寄存器中，它们的
  名字为 %ymrnO~ %ymrn 15 。每个 YMM 寄存器都是 256 位 ( 32 字 节）。当对标最数据操作时，
  这些寄存器只保存浮点数，而且只使用低 32 位（对千
  fl oa t) 或 64 位（对于 double) 。汇
  编代码用寄存器的 SSE XMM 寄存器名字 %xmrn0~ %xmrn15 来引用它们，每个 XMM 寄存器
  都是对应的 YMM 寄存器的低 128 位