alias:: class invariants, type invariant

- [[class invariant]]是一种用于约束类的对象的[[invariant]]。*类的方法* 应该保持[[invarint]]。类不变式约束了对象中存储的状态。
- 类不变式在[[构造]]过程中建立，且在 *[[public]]方法* 的调用之间一直保持。函数内部的代码可能会破坏 invariant，只要在 public 函数结束之前恢复 invariant 即可。
  id:: 6534c65e-afbb-435a-9435-cae6766a8d94
  在[[并发]]情况下维持 invariant ，通常需要使用[[mutex]]来通过锁定状态来维护方法中的。
-