alias:: 静态调用桥梁

- 在 Unity 中，静态调用桥梁（Static Call Bridge）是一种设计模式，用于在不同的脚本和模块之间建立松散耦合的连接，通常用于事件系统、消息传递或服务定位等场景。它利用静态方法和事件来简化跨脚本或模块的调用，避免直接引用导致的紧耦合。
- 下面是一个简单的示例，展示如何实现和使用静态调用桥梁。
- ### 定义静态调用桥梁类 
  logseq.order-list-type:: number
- 创建一个静态类来管理事件和方法调用。这个类将充当桥梁，允许其他脚本通过它进行通信。
  ```csharp
  using System;
  
  public static class StaticCallBridge
  {
    // 定义一个事件，用于消息传递
    public static event Action<string> OnMessageReceived;
  
    // 调用事件的方法
    public static void SendMessage(string message)
    {
        OnMessageReceived?.Invoke(message);
    }
  }
  ```
- ### 发送消息 
  logseq.order-list-type:: number
- 在需要发送消息的脚本中，通过静态调用桥梁发送消息。
  ```csharp
  using UnityEngine;
  
  public class MessageSender : MonoBehaviour
  {
    void Start()
    {
        // 发送消息
        StaticCallBridge.SendMessage("Hello from MessageSender!");
    }
  }
  ```
- ### 接收消息 
  logseq.order-list-type:: number
- 在需要接收消息的脚本中，订阅静态调用桥梁的事件。
  ```csharp
  using UnityEngine;
  
  public class MessageReceiver : MonoBehaviour
  {
    void OnEnable()
    {
        // 订阅消息事件
        StaticCallBridge.OnMessageReceived += HandleMessage;
    }
  
    void OnDisable()
    {
        // 取消订阅消息事件
        StaticCallBridge.OnMessageReceived -= HandleMessage;
    }
  
    // 处理接收到的消息
    void HandleMessage(string message)
    {
        Debug.Log("Message received: " + message);
    }
  }
  ```
- ### 完整示例 
  logseq.order-list-type:: number
- 将所有代码片段整合在一起，创建一个简单的 Unity 项目，包含两个脚本：`MessageSender` 和 `MessageReceiver`，分别用于发送和接收消息。
- #### StaticCallBridge.cs
  ```csharp
  using System;
  
  public static class StaticCallBridge
  {
    public static event Action<string> OnMessageReceived;
  
    public static void SendMessage(string message)
    {
        OnMessageReceived?.Invoke(message);
    }
  }
  ```
- #### MessageSender.cs
  ```csharp
  using UnityEngine;
  
  public class MessageSender : MonoBehaviour
  {
    void Start()
    {
        StaticCallBridge.SendMessage("Hello from MessageSender!");
    }
  }
  ```
- #### MessageReceiver.cs
  ```csharp
  using UnityEngine;
  
  public class MessageReceiver : MonoBehaviour
  {
    void OnEnable()
    {
        StaticCallBridge.OnMessageReceived += HandleMessage;
    }
  
    void OnDisable()
    {
        StaticCallBridge.OnMessageReceived -= HandleMessage;
    }
  
    void HandleMessage(string message)
    {
        Debug.Log("Message received: " + message);
    }
  }
  ```
- ### 使用场景
- 静态调用桥梁可以用于各种场景，包括但不限于：
	- **事件系统**：集中管理全局事件的订阅和发布，避免各脚本之间的直接引用。
	- **服务定位器**：提供一个中心点，通过静态方法获取服务实例，简化服务的访问。
	- **消息传递**：实现模块之间的松散耦合通信，提升代码的可维护性和扩展性。
- 这种模式在需要全局访问某些功能或状态时非常有用，但也需要注意避免过度使用静态方法和事件，导致代码难以测试和调试。合理设计和使用静态调用桥梁，可以大大提升项目的组织和维护效率。
  <!--Converted by ToLogseq-->