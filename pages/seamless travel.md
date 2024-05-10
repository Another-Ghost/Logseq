alias:: 无缝切换, 无缝切换, 无缝切换关卡

- ## 启用无缝切换
	- 要启用无缝切换，需要设置一个[[过渡地图]]。
		- 这需要通过 `UGameMapsSettings::TransitionMap` 属性进行配置。
		  该属性默认为空，如果您的游戏保持这一默认状态，就会为过渡地图创建一个空地图。
	- 之所以存在过渡地图，是因为必须始终有一个被加载的世界（用于存放地图），所以在加载新地图之前，我们不能释放原有的地图。由于地图可能会非常大，因此让新旧地图同时存放在存储器内绝对是个坏主意，这时就需要过渡地图来帮忙了。
	- 现在，我们可以从当前地图转移到过渡地图，然后可以从那里转移到^^最终的地图^^。由于**过渡地图非常小**，因此在"中转"当前地图和最终地图时不会造成太大的资源消耗。
		- 设置好过渡地图后，需要将 `AGameModeBase::bUseSeamlessTravel` 设置为 true，这样就可以实现[[无缝切换]]了。
- ## 无缝切换流程
  下面是执行无缝切换时的一般流程：
	- 标记出^^要在[[过渡关卡]]中存留的 actor^^ ；
	  logseq.order-list-type:: number
	- 转移到过渡关卡；
	  logseq.order-list-type:: number
	- 标记出^^要在[[最终关卡]]中存留的 actor^^；
	  logseq.order-list-type:: number
	- 转移到最终关卡。
	  logseq.order-list-type:: number
- ## 无缝切换中的 [[Persisting Actor]]
	- 在使用无缝切换时，可以将（存留） actor 从当前关卡带到新的关卡。这适用于一些特定的 actor，如道具栏物品和玩家等。
	- 默认情况下，这些 actor 将自动存留：
		- [[GameMode]] actor（仅限服务器）
			- 通过 [[AGameModeBase::GetSeamlessTravelActorList]] 额外添加的任何 actor
		- 拥有一个有效的 [[PlayerState]] （仅限服务器）的所有[[Controller]]
		- 所有 [[PlayerController]] （仅限服务器）
	- 所有[[local PlayerController]] （服务器和客户端）
		- 通过 [[APlayerController::GetSeamlessTravelActorList]] （在本地`PlayerControllers`上调用）额外添加的任何 actor 。