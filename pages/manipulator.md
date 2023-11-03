alias:: 操控器

- IOStream程序库中最重要的一些 [[manipulator]]：
  |manipulator|类|描述|
  |--|--|--|
  |endl|ostream|输出 `\n`，并刷新[[output缓冲区]]|
  |ends|ostream|输出 `\0`|
  |flush|ostream|刷新[[output缓冲区]]|
  | ws|istream|读入并忽略空白字符[[whitespace]] |
- 刷新output缓冲区：（也就是对于给定的stream，应用其flush
  （）强制输出缓冲区内所有数据）。