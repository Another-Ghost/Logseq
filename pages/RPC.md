alias:: RPCs, Remote Procedure Call, 远程过程调用, replicated function, 远程方法调用

- [[远程过程调用]]可以从任何机器上调用，但将其实际执行定向到连接到网络会话的特定机器上。有三种类型的RPC可用：
  |RPC类型|说明|
  |--|--|
  |[[Server]]|仅在主持游戏的[[服务器]]上调用。|
  |[[Client]]|仅在拥有 该函数所属Actor 的[[客户端]]上调用。若Actor没有连接，将不会执行此逻辑。|
  |[[NetMulticast]]|在与服务器连接的**所有**[[客户端]]及[[服务器]]本身上调用。|
- 可以通过在C++中函数的[UFUNCTION]]宏中提供`Server`、`Client`或`NetMulticast`修饰符将其指定为RPC。函数的实现在其名字中添加后缀 `_Implementation`。
  id:: 653d134a-d1d4-46cc-933e-dd3eeb2d4cfb
- `ExampleClass.h`
  ``` cpp 
  //服务器RPC MyFunction的声明。
    UFUNCTION(Server, Reliable, WithValidation)
    void MyFunction(int myInt);
  ```
  `ExampleClass.cpp`
  ```cpp 
  //服务器RPC MyFunction的实现。
    void AExampleClass::MyFunction_Implementation(int myInt)
    {
        //Gameplay代码
    }
  ```
- 欲了解RPC的更多相关详情，参见[远程过程调用](https://docs.unrealengine.com/5.3/zh-CN/rpcs-in-unreal-engine)指南。
- ## Reliability
	- 您必须将[[RPC]]标记为[[reliable]]或[[unreliable]]。
	  在蓝图中，默认情况下，函数和事件被假定为[[unreliable]]。通过在详细面板中将可靠性设置为 `true`，您可以将函数标记为可靠。在C++中，您必须在任何[[RPC]]的[[UFUNCTION]]宏中添加[[Reliable]]或[[Unreliable]]修饰符。
	- [[不可靠]]的RPC**不能保证到达其预定目的地**，但不同于[[可靠]]的RPC，它们可以**更快速**和**更频繁地发送**。
	  id:: 653d160b-0be4-43f1-bf7d-953320b36005
	  它们最**适用于**对游戏不关键的功能，或者被非常频繁地调用的功能。
	  例如，Actor的移动使用不可靠的RPC进行复制，因为它可以在每帧中发生变化。
	- [[可靠]]的RPC被保证到达其预定目的地，并在被成功接收之前一直保留在[[队列]]中。它们最**适用于**对游戏关键的功能，但不经常调用的功能。这些功能的示例包括[[碰撞事件]]、开始或结束武器射击，或[[生成Actor]]。
	- #+BEGIN_WARNING
	  滥用[[可靠]]函数可能导致其[[队列]]溢出，这将导致强制断开连接。若**逐帧调用复制函数**，应将其设为[[不可靠]]。若拥有与玩家[[输入]]绑定的[[可靠]]函数，应**限制玩家调用该函数的频率**。
	  #+END_WARNING
- ## Validation
	- `WithValidation` 说明符表明除函数的实现外，还有 可验证传入函数的 *数据* 的 函数。此 *验证函数* 与其负责的函数使用同一[[签名]]，但其将返回`bool`而非原本 *返回值* 。若返回 `true`，则其允许执行RPC的 `Implementation`；若返回 `false`，则阻止执行。
	- `ExampleClass.cpp`
	  ``` cpp
	  //服务器RPC MyFunction的验证
	      bool AExampleClass::MyFunction_Validation(int myInt)
	      {
	          /*
	              若myInt的值为负，建议不允许运行MyFunction_Implementation。
	              因此仅在myInt大于零时返回true。
	          */
	          return myInt >= 0;
	      }
	  ```
-