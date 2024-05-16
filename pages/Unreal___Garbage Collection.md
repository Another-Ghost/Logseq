alias:: Unreal GC

- 虚幻实现垃圾回收机制，不再被引用或已被显式标记为销毁的[[UObject]]将定期清除。
  引擎构建一个[[reference graph]]以确定哪些`UObject`仍在使用，哪些是孤立的。
  在该 graph 根部是一组指定为[[root set]]的`UObject`。任何`UObject`都可以添加到根集。
  当进行垃圾回收时，引擎将从根集开始，搜索已知`UObject`引用树来跟踪所有引用的`UObject`。任何未被引用的`UObject`（意味着未在树搜索中找到这些对象）将被假设为不再需要，因此被删除。
- ### UPROPERTY
	- 你通常需要用一个[[UObject]]的[[UPROPERTY]]引用来保持其存活，这个 UObject 可以是一个 UObject pointer 或者存储 UObject pointer 的 [[Unreal/Container]] 类，如[[TArray]]
	- [[Actor]] 及其 [[组件]] 通常属于例外情况，因为Actor通常被**链接到 [[root set]]的 Object**所引用（例如它们所属的 [[Level]] ），而 Actor 的 component 被 Actor 自身引用。
		- Actor可以显式标记为销毁，方法是调用它们的`Destroy`函数，这是从进行中游戏移除Actor的标准方法。
		- 组件可以使用[[UActorComponent::DestroyComponent]]函数显式销毁，但它们通常在拥有它们的 Actor 从游戏中移除时被销毁。
- 虚幻引擎4中的垃圾回收速度快，效率高，内置大量的优化功能，能够尽量降低开销，如[[多线程可访问性分析]]可以标识 孤立 Object ，[[unhashing code]] 优化了从容器中移除 Actor 的速度。
- 还有一些其他功能以调节，以更精准地控制如何以及何时执行垃圾回收，大部分都可以在 **项目设置（Project Settings）** 中的 **引擎 - 垃圾回收（Engine - Garbage Collection）** 下找到。以下设置通常用于为项目调节垃圾回收器性能：
- ## 集群处理
	- 虚幻引擎中的垃圾回收过程将构建要一并销毁的 object 的 [[cluster]] 。较之于单个删除对象， ^^[[群集]]处理^^可减少垃圾回收相关的总时间和整体[[内存抖动]]。 
	  随着对象加载，可能创建子对象。将对象与其子对象组合到单个[[cluster]]后，引擎可延迟释放群集使用的资源，直到**整个对象**可被释放时一次性释放全部资源。
- ## Reference
	- https://dev.epicgames.com/documentation/zh-cn/unreal-engine/garbage-collection-settings-in-the-unreal-engine-project-settings
	- https://dev.epicgames.com/documentation/zh-cn/unreal-engine/unreal-engine-actor-lifecycle
-