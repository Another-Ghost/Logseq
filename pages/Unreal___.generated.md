public:: false

- 在 Unreal Engine 中，`.generated` 文件是 Unreal Header Tool（UHT）生成的一组代码文件。这些文件负责实现引擎的反射系统。UHT 会扫描源代码中的特殊宏（如 `UCLASS()`、`USTRUCT()`、`UPROPERTY()`、`UFUNCTION()` 等），并为这些标记生成相应的元数据和辅助代码。这些文件通常有 `.generated.h` 后缀，并且在项目编译时自动生成。
- 以下是对 `.generated` 文件和其作用的详细解释：
- ### `.generated.h` 文件的作用 
  logseq.order-list-type:: number
  `.generated.h` 文件包含由 UHT 生成的代码，这些代码为类、结构体和枚举提供反射支持。生成的代码使得 Unreal Engine 能够在运行时动态查询和修改对象的属性和函数。这对于蓝图、序列化、网络复制、编辑器扩展等功能至关重要。
- ### UHT（Unreal Header Tool） 
  logseq.order-list-type:: number
  UHT 是一个预处理工具，在常规的 C++ 编译过程之前运行。它会解析所有包含特定宏的头文件，并生成对应的 `.generated.h` 文件。
	- **扫描和解析**：UHT 扫描包含特定宏的头文件，例如 `UCLASS()`、`USTRUCT()`、`UPROPERTY()` 和 `UFUNCTION()`。
	- **生成元数据**：基于这些宏，UHT 生成反射所需的元数据。
	- **输出 `.generated.h` 文件**：这些文件包含类的注册信息、属性的元数据、方法的调用包装器等。
- ### `.generated.h` 文件示例 
  logseq.order-list-type:: number
  考虑以下一个简单的 Unreal 类声明：
  ```cpp
  // MyActor.h
  #pragma once
  
  #include "CoreMinimal.h"
  #include "GameFramework/Actor.h"
  #include "MyActor.generated.h"
  
  UCLASS()
  class MYGAME_API AMyActor : public AActor
  {
    GENERATED_BODY()
  
  public:
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="Test")
    int32 MyProperty;
  
    UFUNCTION(BlueprintCallable, Category="Test")
    void MyFunction();
  };
  ```
- 对于这个头文件，UHT 会生成一个对应的 `.generated.h` 文件，通常包含以下内容：
  ```cpp
  // MyActor.generated.h
  
  #pragma once
  
  #include "UObject/ObjectMacros.h"
  #include "UObject/ScriptMacros.h"
  
  // 自动生成的代码，这里省略了大部分内容
  class MYGAME_API AMyActor : public AActor
  {
    GENERATED_BODY()
  
  public:
    static void StaticRegisterNativesAMyActor();
    UClass* GetClass() const override;
  
    // 其他自动生成的元数据和方法
  };
  ```
- ### `GENERATED_BODY` 宏 
  logseq.order-list-type:: number
  `GENERATED_BODY` 宏在类定义中起到关键作用。它会插入由 UHT 生成的代码，这些代码实现了反射系统所需的各种功能。
	- **类的注册**：每个包含 `GENERATED_BODY` 宏的类都会在引擎启动时注册到全局类列表中，这使得引擎可以在运行时查询和创建这些类的实例。
	- **属性和方法的元数据**：属性和方法的反射元数据会被添加到类的定义中，使得引擎能够在运行时访问这些元数据。
- ### 编译过程中的角色 
  logseq.order-list-type:: number
	- **头文件扫描**：在编译项目时，UHT 首先扫描所有包含特定宏的头文件。
	- **生成 `.generated.h` 文件**：根据扫描结果，UHT 生成对应的 `.generated.h` 文件，这些文件包含反射系统所需的代码。
	- **编译和链接**：常规的 C++ 编译器（如 Clang 或 MSVC）然后编译这些生成的文件，并将它们链接到最终的二进制文件中。
- ### 开发者注意事项 
  logseq.order-list-type:: number
	- **手动编辑警告**：`.generated.h` 文件是自动生成的，不应手动编辑。任何对这些文件的更改都会在下次编译时被覆盖。
	- **包含顺序**：确保在类定义头文件中包含 `.generated.h` 文件，这是 UHT 生成的代码能够正常工作的必要条件。
- 通过这些机制，Unreal Engine 实现了强大的反射系统，支持蓝图、序列化、网络同步等高级功能，为开发者提供了极大的灵活性和便利。
  <!--Converted by ToLogseq-->