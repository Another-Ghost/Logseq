alias:: GNU Compiler Collection

- [[GCC driver]]
- |选项|描述|
  |--|--|
  |-S|只[[编译]]，不[[汇编]]和[[链接]]。|
  |-o <file>|输出到 <file>|
  |-static|告诉[[GCC Driver]]，[[链接器]]应该构建一个 *完全链接的* [[可执行目标文件]]，它可以加载到内存并运行，在加载时**无须更进一步的链接**。|
  |-fpic |指示[[编译器]]生成与[[位置无关代码]]。|
  |-shared| 选项指示[[链接器]]创建一个[[共享目标文件]]。|
-