alias:: FTimerManager, 全局定时器管理器, Timer Manager, 定时器管理器

- ^^全局定时器管理器^^存在于 [[Game Instance]] 对象上以及每个 [[World]] 中。
- 全局定时器管理器可以用于与任何特定[[World]]的存在没有相关性或依赖性的函数调用。
- ### 定时器速率
	- `FTimerManager`有一个函数`GetTimerRate`，它用于从定时器句柄获取定时器的当前速率（两次激活之间的时间）。定时器速率不能直接更改，但可以使用其定时器句柄调用`SetTimer`来清空定时器并创建新定时器，新定时器除了速率不同，其他保持不变。如果定时器句柄无效，则`GetTimerRate`将返回值`-1`。
-