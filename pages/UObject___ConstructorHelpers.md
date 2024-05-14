- 可用于访问一些有用的构造函数以便设置组件。
- ```cpp
  //https://dev.epicgames.com/documentation/zh-cn/unreal-engine/multiplayer-programming-quick-start-for-unreal-engine
       static ConstructorHelpers::FObjectFinder<UParticleSystem> DefaultExplosionEffect(TEXT("/Game/StarterContent/Particles/P_Explosion.P_Explosion"));
       if (DefaultExplosionEffect.Succeeded())
       {
           ExplosionEffect = DefaultExplosionEffect.Object;
       }
  ```
-