## 可配置的进入运行模式（Configurable Enter Play Mode）
	- 运行模式是 Unity 的核心功能之一。借助运行模式，可通过[工具栏](https://docs.unity3d.com/cn/current/Manual/Toolbar.html) 中的 Play 按钮直接在 Editor 中运行项目。进入运行模式时，项目将像构建后一样启动并运行。退出运行模式时，运行模式期间在 Editor 中所做的任何更改都会重置。
	  
	  在 Editor 中进入运行模式时，Unity 将执行两项重要操作，以确保项目在 Editor 中的启动方式与在构建后的启动方式相同：
		- 重置脚本状态（也称为域重新加载（domain reload））
		- 重新加载场景
	- 执行这两个操作需要花费一些时间，并且随着脚本和场景变得越来越复杂，时间也会随之增加。