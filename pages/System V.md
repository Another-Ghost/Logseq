alias:: System V IPC 机制

- ### [[System V IPC 权限检查机制]]
	- System V进程间通信通常指宏内核下三种具体的进程间通信机制，即[[System V 消息队列]]、[[System V 信号量]]和[[System V 共享内存]]。在 Linux 等系统中，这三种机制通常共享一套权限管理方法。
	- 在 Linux 等宏内核系统中，System V通信的权限管理基于[[文件的权限检查机制]]。
	  [[权限检查]]机制通常依赖于进程的用户分类（所有者用户/用户组用户/其他用户)，并且是基于文件的权限抽象（可读/可写/可执行）来判定的。每个文件都会存储一个根据三类用户以及三种可能的权限组合而成的访问模式（Mode）。
	  进程访问（如读操作)文件时，系统内核会判断这个进程是不是该文件的所有者(Owner),或者是否可以访问该文件的组(Group)中的成员，然后再根据其用户分类检查对应分类下的权限。
	- 将上述权限检查机制应用到进程间通信场景时，内核会将[[通信连接]]抽象成一个个具体[[内核对象]]，比如对消息队列而言，在内核中会有多个[[消息队列]]的对象存在。
	  在通信连接上的操作，如发送消息、接收消息，都会被抽象成对内核对象的访问行为。
	- 如在消息队列的设计中，发送消息相当于对消息队列对象的写操作，而接收消息相当于对消息队列的
	  读操作。这样一来，只要 Linux 内核能够为每个通信的对象准备一个类似文件中的“访问模式”，就可以根据它来检查进程的操作是否合法。
	- 这个“访问模式”的内容，就是 Linux 内核中负责进程间通信权限管理的 `IPC_PERM` 结构。
	  `IPC_PERM` 中的内容如代码所示。整个结构体的内容其实很简单，可以从名字推测出大部分基本含义。主要内容是所有者、创建者的用户和组标识符，以及访问模式。和检查文件访问权限的操作相同，内核会根据用户进程的用户和组信息，再结合内核对象中的信息，对操作进行检查。此外，该结构体中的 `key` 是 System V IPC 对象 的标识符。进程可以根据 `key` 来索引 IPC对象（或IPC连接）。
	  ``` c
	  struct ipc_perm
	  {
	      key_t key;
	      uidt uid;	// 所有者的uid和gid
	      gid_t gid;
	      uid_t cuid; // 创建者的uid和gid
	      gid_t cgid;
	      mode_t mode;// 访问模式
	  }
	  ```
	-