alias:: 垃圾回收, 垃圾收集

- 对于对象内存管理，虚幻引擎提供了如下两个解决方案：
	- 继承自[[UObject]]类，同时指向UObject类实例对象的指针成员变量，使用[[UPROPERTY]]宏进行标记。虚幻引擎的UObject架构会自动地被UProperty标记的变量 考虑到垃圾回收系统中，自动地进行对象的生命周期管理。
	  logseq.order-list-type:: number
	- 采[[用智能指针]]。请注意，只有非UObject类型 ，才能够使用智能指针进行自动内存释放。关于智能指针的讨论，请看本书后面的章节。
	  logseq.order-list-type:: number