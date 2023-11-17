alias:: Amdahl 定律

- [[Amdahl 定律]]的主要思想是，当我们对系统的某个部分加速时，其对系统整体性能的影响取决于该部分的重要性和加速程度。若系统执行某应用程序需要时间为 $T_\text{old}$ 。 假设系统某部分所需执行时间与该时间的比例为 $\alpha$ , 而该部分性能提升比例为 $K$ 。即该部分初始所需时间为 $\alpha T_\text{oId}$ , 现在所
  id:: 65575344-dadb-47d5-8825-b19632c06fed
  需时间为 $(\alpha T_\text{old}) / k$ 。因此，总的执行时间应为
  $$T_{un}=(1-a)T_{ut}+(aT_\text{old})/k=T_{ut}[(1-a)+a/k]$$
- 由此可计算加速比 $S$ ：
  $$S=\frac{T_\text{old}}{T_\text{new}}=\frac{1}{(1-a)+a/k}$$