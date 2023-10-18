alias:: Unreal Build Tool

- 大致而言，UBT的工作分为三个阶段：
	- 收集阶段
	  logseq.order-list-type:: number
	  收集信息。UBT收集环境变量、虚幻引擎源代码目
	  录、虚幻引擎目录、工程目录等一系列的信息。
	- 参数解析阶段 
	  logseq.order-list-type:: number
	  UBT解析传入的命令行参数，确定自己需要生成
	  的目标类型。
	- 实际生成阶段
	  logseq.order-list-type:: number
	  UBT根据环境和参数，开始生成makefile，确定
	  C++的各种目录的位置。最终开始构建整个项目。此时编译工作交
	  给标准C++编译器。