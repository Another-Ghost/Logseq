alias:: UPROPERTY

- 在 Unreal Engine 中，`UProperty` 宏已经在较新版本的 Unreal Engine 4.25 以及 Unreal Engine 5 中被 `FProperty` 替代。原先的 `UProperty` 用于声明类的成员变量，以便它们可以由 Unreal Engine 的**编辑器和其运行时系统使用（例如在蓝图中访问），或者用于[[序列化]]和[[网络复制]]**。
  id:: 6645fa91-73ff-46d8-b998-5de17dc25fec
- 对于非 `UObject` 的普通 C++ 对象，你可以使用 `UPROPERTY`（现在为 `FProperty`）宏来确保这些成员变量可以被 Unreal Engine 正确处理。这包括结构体 (`FStruct`)、枚举 (`UEnum`)、简单的数据类型（如 `int32`、`float`、`bool` 等），以及其他非 `UObject` 类型，如 `FString` 和 `TArray`。
- ### 基本使用
- 在类定义中，你可以这样声明这些属性：
  ```cpp
  #include "CoreMinimal.h"
  #include "GameFramework/Actor.h"
  #include "MyActor.generated.h"
  
  UCLASS()
  class MYGAME_API AMyActor : public AActor
  {
    GENERATED_BODY()
  
  public:
    // 普通的整数属性
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="My Category")
    int32 MyInt;
  
    // 字符串属性
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="My Category")
    FString MyString;
  
    // 结构体属性
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="My Category")
    FTransform MyTransform;
  
    // 数组属性
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="My Category")
    TArray<int32> MyArray;
  };
  ```
- ### 注意事项
	- `UPROPERTY()` 宏在非 `UObject` 的成员变量上使用时，需要注意成员的类型是否支持 Unreal 的反射系统。基本数据类型和 Unreal 提供的一些数据结构（如 `FVector`、`FRotator` 等）都是支持的。
	- 自定义的结构体需要用 `USTRUCT()` 宏来定义，以确保它们也可以被 Unreal Engine 的系统正确处理。
- ### 自定义结构体示例
	- 如果你有一个自定义结构体并希望在 Unreal 中使用，你应该这样声明：
	  ```cpp
	  #include "MyStruct.generated.h"
	  
	  USTRUCT(BlueprintType)
	  struct FMyStruct
	  {
	    GENERATED_BODY()
	  
	    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="My Struct Category")
	    int32 StructMember;
	  };
	  ```
	- 然后在你的类中使用这个结构体：
	  ```cpp
	  UCLASS()
	  class MYGAME_API AMyActor : public AActor
	  {
	    GENERATED_BODY()
	  
	  public:
	    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="My Category")
	    FMyStruct MyCustomStruct;
	  };
	  ```
-