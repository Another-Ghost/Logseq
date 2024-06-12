alias:: coroutine

- 在 Unity 中，协程（Coroutine）是用于处理需要跨帧执行的任务的强大工具。协程允许你编写可以在多个帧中运行的代码，这对于处理异步任务（如加载资源、等待时间、动画等）非常有用。以下是关于协程的一些基本概念和使用示例。
- ### 基本概念
	- **协程方法**：协程方法通常返回 `IEnumerator` 类型，并使用 `yield return` 语句来控制协程的执行。
	- **启动协程**：使用 `MonoBehaviour` 的 `StartCoroutine` 方法来启动协程。
	- **停止协程**：使用 `StopCoroutine` 或 `StopAllCoroutines` 方法来停止协程。
- ### 基本用法
  以下是一个简单的协程示例，它展示了如何启动和停止协程，以及如何在协程中使用 `yield return` 语句。
	- #### 示例：简单的协程
	  ```csharp
	  using UnityEngine;
	  using System.Collections;
	  
	  public class CoroutineExample : MonoBehaviour
	  {
	  void Start()
	  {
	      // 启动协程
	      StartCoroutine(PrintMessages());
	  }
	  
	  IEnumerator PrintMessages()
	  {
	      Debug.Log("Message 1");
	      // 等待 2 秒
	      yield return new WaitForSeconds(2.0f);
	      
	      Debug.Log("Message 2");
	      // 等待 3 秒
	      yield return new WaitForSeconds(3.0f);
	      
	      Debug.Log("Message 3");
	  }
	  }
	  ```
	  在这个示例中，`PrintMessages` 是一个协程方法，它会在 2 秒后打印第二条消息，然后在 3 秒后打印第三条消息。
- ### 常见用途
	- #### 处理异步任务 
	  logseq.order-list-type:: number
	  协程可以用于处理需要等待的任务，例如从服务器加载数据或等待玩家输入。
	  ```csharp
	  using UnityEngine;
	  using UnityEngine.Networking;
	  using System.Collections;
	  
	  public class LoadDataExample : MonoBehaviour
	  {
	  void Start()
	  {
	      // 启动协程来加载数据
	      StartCoroutine(LoadDataFromServer("https://example.com/data.json"));
	  }
	  
	  IEnumerator LoadDataFromServer(string url)
	  {
	      UnityWebRequest request = UnityWebRequest.Get(url);
	      yield return request.SendWebRequest();
	  
	      if (request.result == UnityWebRequest.Result.ConnectionError || request.result == UnityWebRequest.Result.ProtocolError)
	      {
	          Debug.LogError("Error: " + request.error);
	      }
	      else
	      {
	          // 处理加载的数据
	          Debug.Log("Data Loaded: " + request.downloadHandler.text);
	      }
	  }
	  }
	  ```
	- #### 等待条件 
	  logseq.order-list-type:: number
	  你可以使用协程等待特定条件满足。
	  ```csharp
	  using UnityEngine;
	  using System.Collections;
	  
	  public class WaitForConditionExample : MonoBehaviour
	  {
	  private bool isConditionMet = false;
	  
	  void Start()
	  {
	      // 启动协程来等待条件满足
	      StartCoroutine(WaitForCondition());
	      
	      // 模拟条件在 5 秒后满足
	      StartCoroutine(SimulateCondition());
	  }
	  
	  IEnumerator WaitForCondition()
	  {
	      // 等待条件满足
	      yield return new WaitUntil(() => isConditionMet);
	      
	      Debug.Log("Condition met! Continuing...");
	  }
	  
	  IEnumerator SimulateCondition()
	  {
	      // 等待 5 秒
	      yield return new WaitForSeconds(5.0f);
	      
	      isConditionMet = true;
	  }
	  }
	  ```
- ### 停止协程
  你可以使用 `StopCoroutine` 方法停止一个正在运行的协程，或者使用 `StopAllCoroutines` 方法停止所有协程。
  ```csharp
  using UnityEngine;
  using System.Collections;
  
  public class StopCoroutineExample : MonoBehaviour
  {
    private Coroutine myCoroutine;
  
    void Start()
    {
        // 启动协程并保存其引用
        myCoroutine = StartCoroutine(PrintMessages());
    }
  
    void Update()
    {
        // 按下空格键停止协程
        if (Input.GetKeyDown(KeyCode.Space))
        {
            StopCoroutine(myCoroutine);
            Debug.Log("Coroutine stopped.");
        }
    }
  
    IEnumerator PrintMessages()
    {
        while (true)
        {
            Debug.Log("Message");
            yield return new WaitForSeconds(1.0f);
        }
    }
  }
  ```
- ### 总结
  协程是 Unity 中处理异步操作的有力工具。它们允许你在多个帧中执行代码，而不会阻塞主线程。通过使用 `StartCoroutine` 启动协程和 `yield return` 控制协程的执行，你可以轻松地实现复杂的时间管理和异步操作。
  <!--Converted by ToLogseq-->