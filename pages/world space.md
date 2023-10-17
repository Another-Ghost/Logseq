id:: 64d53330-edd2-4d54-ad10-9bd9cd0e21db
alias:: world coordinate, world coordinates, 世界空间, 世界坐标系

- [[世界空间]]的 $x$ *轴*，$y$ *轴*，$z$ *轴* 是固定不变的。
- 如果一个[[transform]]没有任何[[父坐标空间]]，那么这个[[position]], [[rotation]], [[sacle]]就是定义在[[世界坐标系]]中的。
  这是因为相当于还有一个 *虚拟的* [[根模型]]，这个根模型的[[模型空间]]就是[[世界空间]]。