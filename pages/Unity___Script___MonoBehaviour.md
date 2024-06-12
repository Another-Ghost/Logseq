alias:: MonoBehaviour

- ^^MonoBehaviour^^类是一个基类，所有 [[Unity 脚本]]都默认派生自该类。当从 Unity 的项目窗口创建一个C\#脚本时，它会自动继承MonoBehaviour，并提供模板脚本。
- MonoBehaviour 类提供了框架，允许将脚本附加到编辑器中的游戏对象，并提供诸如 Start 和 Update 等常用事件的挂钩。
- ### 协程
  MonoBehaviour 类允许启动、停止和管理协程，这是一种编写异步代码的方法，其中包括等待一定时间或某些操作完成，同时允许其他代码继续执行。
	- https://docs.unity3d.com/cn/2022.3/Manual/Coroutines.html
	- https://docs.unity3d.com/cn/2022.3/ScriptReference/MonoBehaviour.StartCoroutine.html
- ## 事件
	- `Start`-在游戏对象开始存在时（加载场景或实例化游戏对象时）调用。
	- `Update`-每帧都会被调用。
	- `FixedUpdate`- 每个物理时间步进调用。
	- `OnBecameVisible` 和 `OnBecameInvisible` - 当游戏对象的渲染器进入或离开摄像机的视图时调用。
	- `OnCollisionEnter` 和 `OnTriggerEnter` - 在发生物理碰撞或触发时调用。
	- `OnDestroy` - 在销毁游戏对象时调用。
	- ### [[OnMouseDown]]
	  当用户在 [Collider](https://docs.unity3d.com/cn/current/ScriptReference/Collider.html) 上按下鼠标按钮时，将调用 [OnMouseDown](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnMouseDown.html)。
- ## Reference
	- https://docs.unity3d.com/cn/2022.3/Manual/CreatingAndUsingScripts.html
	- https://docs.unity3d.com/cn/2022.3/ScriptReference/MonoBehaviour.html
	-