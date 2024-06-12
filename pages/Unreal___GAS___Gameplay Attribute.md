alias:: Gameplay Attribute, 游戏属性, FGameplayAttributeData

- [[Gameplay Ability System]]使用 ^^Gameplay Attribute^^ 来保存、计算和修改与游戏相关的**浮点值**。
  这些值可以描述其拥有者的任何特征，比如角色的剩余生命值，车辆的最高速度，或者物品在损坏前可以使用的次数。
- 游戏技能系统中的角色将他们的游戏属性存储在一个 [[Attribute Set]] 中，该属性集有助于管理Gameplay Attribute 与系统其他部分之间的交互，并将自己^^注册^^到角色的[[技能系统组件]]中。这些交互包括**对数值范围的限定、临时数值变更、对永久改变基础值的事件做出反应**等。
- 游戏属性会保持一个 [[Current Value]] 和 [[base value]] ，current value 是大多数计算和逻辑会使用的值，并且会受到当前激活的[[gameplay effect]]的影响，而base value则倾向在较长时间内保持固定。
	- 举个例子，"跳跃高度"游戏玩法属性的基础值可能是100.0，但如果该角色有一个主动的[游戏玩法效果]，显示角色累了，只能跳到正常高度的70%，那么当前值就是70.0。如果该角色发生永久性改变，变得更善于跳跃，这可能是通过等级提升系统实现的，那么基础值可能会增加到110.0，而只要[[Gameplay Effect]]还在，当前值就会被计算为77.0。
- 要创建游戏属性，你必须首先新建一个[[属性集]]（Attribute Set）。然后你就可以将游戏属性添加到属性集中。
- ## 生成默认辅助函数的宏
	- | 宏（带参数）|生成函数的签名|行为/用途|
	  | `GAMEPLAYATTRIBUTE_PROPERTY_GETTER(UMyAttributeSet, Health)` | `static FGameplayAttribute GetHealth()` | 静态函数从虚幻引擎的反射系统中返回`FGameplayAttribute`结构 |
	  | `GAMEPLAYATTRIBUTE_VALUE_GETTER(Health)` | `float GetHealth() const` | 返回"生命值"游戏玩法属性的当前值 |
	  | `GAMEPLAYATTRIBUTE_VALUE_SETTER(Health)` | `void SetHealth(float NewVal)` | 将"生命值"游戏玩法属性的值设置为`NewVal` |
	  | `GAMEPLAYATTRIBUTE_VALUE_INITTER(Health)` | `void InitHealth(float NewVal)` | 将"生命值"游戏玩法属性的值初始化为`NewVal` |
	- 添加完这些之后，你的属性集类定义应该是如下所示：
	  ```cpp
	  	UCLASS()
	  	class MYPROJECT_API UMyAttributeSet : public UAttributeSet
	  	{
	  		GENERATED_BODY()
	   
	  		protected:
	  		/** Sample "Health" Attribute */
	  		UPROPERTY(EditAnywhere, BlueprintReadOnly)
	  		FGameplayAttributeData Health; //FGameplayAttributeData仅存储Gameplay属性数据和提供对游戏玩法属性数据的访问。
	   
	  		//~ ... Other Gameplay Attributes here ...
	   
	  		public:
	  		//~ Helper functions for "Health" attributes
	  		GAMEPLAYATTRIBUTE_PROPERTY_GETTER(UMyAttributeSet, Health);
	  		GAMEPLAYATTRIBUTE_VALUE_GETTER(Health);
	  		GAMEPLAYATTRIBUTE_VALUE_SETTER(Health);
	  		GAMEPLAYATTRIBUTE_VALUE_INITTER(Health);
	   
	  		//~ ... Helper functions for other Gameplay Attributes here ...
	  	};
	  
	  ```
	- 虽然你可以不使用辅助函数，但它们是最佳做法。
- ## 与 [[Gameplay Effect]] 交互
  对 Gameplay Attribute 的值进行控制的常见方法是处理与之相关的 Gameplay Effect 。
	- 首先在 [[Attribute Set]] 的类定义中覆盖`PostGameplayEffectExecute`函数，该函数应该是 public 的。
	  logseq.order-list-type:: number
	  ```cpp
	   void PostGameplayEffectExecute(const struct FGameplayEffectModCallbackData& Data) override;
	  ```
	- 在 Attribute Set 的源文件中编写函数主体，**务必要调用父类的执行**。
	  logseq.order-list-type:: number
	  ```cpp
	   void UMyAttributeSet::PostGameplayEffectExecute(const struct FGameplayEffectModCallbackData& Data)
	   {
	       // 记得要调用父类的执行。
	       Super::PostGameplayEffectExecute(Data);
	   
	       // 通过使用属性获取器来查看这个调用是否会影响生命值。
	       if (Data.EvaluatedData.Attribute == GetHealthAttribute())
	       {
	           // 这个游戏玩法效果是改变生命值。应用它，但要先限制数值。
	           // 在这种情况下，生命值的基础值不可是负值。
	           SetHealth(FMath::Max(GetHealth(), 0.0f));
	       }
	   }
	  ```
- ## [[Replication]]
  对于多人游戏项目，可以通过^^[[属性集]]复制^^游戏玩法属性，其方式类似于复制其它属性的方式。
	- 首先在属性集标头的 PROPERTY 定义中加入[[ReplicatedUsing]] 说明符，这将设置一个回调函数，有助于在远程系统上进行预测。
	  logseq.order-list-type:: number
	  ```cpp
	   protected:
	   /** Sample "Health" Attribute */
	   UPROPERTY(EditAnywhere, BlueprintReadOnly, ReplicatedUsing = OnRep_Health)
	   FGameplayAttributeData Health;
	  ```
	- 声明你的复制回调函数：
	  logseq.order-list-type:: number
	  ```cpp
	   /** 当新的生命值达到网络时被调用 */
	   UFUNCTION()
	   virtual void OnRep_Health(const FGameplayAttributeData& OldHealth);
	  
	  ```
	- 在属性集的源文件中，定义你复制的回调函数。函数的主体可以用 GAS 定义的一个宏 `GAMEPLAYATTRIBUTE_REPNOTIFY` 来表示。
	  logseq.order-list-type:: number
	  ```cpp
	  void UMyAttributeSet::OnRep_Health(const FGameplayAttributeData& OldHealth)
	   {
	       // 使用默认的游戏玩法属性系统更新通知行为。
	       GAMEPLAYATTRIBUTE_REPNOTIFY(UMyAttributeSet, Health, OldHealth);
	   }
	  ```
	- 如果这是你的属性集中的首个复制的属性，你要对 public 的[[GetLifetimeReplicatedProps]]函数设置一个覆盖。
	  logseq.order-list-type:: number
	  ```cpp
	   /** Marks the properties we wish to replicate */
	   virtual void GetLifetimeReplicatedProps(TArray<FLifetimeProperty>& OutLifetimeProps) const override;
	  ```
	- 将游戏玩法属性添加到属性集源文件中的`GetLifetimeReplicatedProps`函数中，如下所示：
	  logseq.order-list-type:: number
	  ```cpp
	  void UMyAttributeSet::GetLifetimeReplicatedProps(TArray<FLifetimeProperty>& OutLifetimeProps) const
	   {
	       // 调用父函数。
	       Super::GetLifetimeReplicatedProps(OutLifetimeProps);
	   
	       // 为生命值添加复制功能。
	       DOREPLIFETIME_CONDITION_NOTIFY(UMyAttributeSet, Health, COND_None, REPNOTIFY_Always);
	   }
	  ```
-