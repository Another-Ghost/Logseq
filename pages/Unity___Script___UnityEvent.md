alias:: UnityEvent

- 在 Inspector 中配置 `UnityEvent` 时，支持两种类型的函数调用：
	- 静态。静态调用是预配置的调用，具有在 UI 中设置的预配置值。这意味着，在调用回调时，使用已在 UI 中输入的参数调用目标函数。
	- 动态。使用从代码发送的参数调用动态调用，并与正在调用的 UnityEvent 类型相关。UI 会过滤回调，仅显示对 UnityEvent 有效的动态调用。
-