- Unity 中的脚本与传统的程序概念不同。在传统程序中，代码在循环中连续运行，直到完成任务。相反，Unity 通过调用在脚本中声明的某些函数来间歇地将控制权交给脚本。函数执行完毕后，控制权将交回 Unity。这些函数由 Unity 激活以响应游戏中发生的事件，因此称为事件函数。
-
- ## 执行顺序
	- https://docs.unity3d.com/cn/current/Manual/ExecutionOrder.html
	- ![monobehaviour_flowchart.svg](../assets/monobehaviour_flowchart_1718163415620_0.svg)
- ## 初始化事件
	- 如果能在游戏运行过程中进行任何更新之前调用初始化代码，通常会很有用。在第一帧之前或开始对象的物理更新之前需要调用 [Start](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.Start.html) 函数。场景加载时会为场景中的每个对象调用 [Awake](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.Awake.html) 函数。请注意，虽然各种对象的 Start 和 Awake 函数的调用顺序是任意的，但在调用第一个 Start 之前，所有 Awake 都要完成。这意味着 Start 函数中的代码可以利用先前在 Awake 阶段执行的其他初始化。
- ## GUI 事件
  Unity 有一个系统用于渲染场景中主要操作的 GUI 控件，并响应对这些控件的点击。此代码的处理方式与正常的帧更新有些不同，因此应将此代码置于定期调用的 [OnGUI](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnGUI.html) 函数中。
  ```
  void OnGUI() {
    GUI.Label(labelRect, "Game Over");
  }
  ```
  此外，还可以检测场景中出现的游戏对象上发生的鼠标事件。使用此功能可以定位武器或显示当前在鼠标指针下的角色的相关信息。借助一系列 OnMouseXXX 事件函数（例如 [OnMouseOver](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnMouseOver.html)、[OnMouseDown](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnMouseDown.html)）可以让脚本对用户的鼠标操作做出反应。例如，如果指针位于特定对象上时按下鼠标按钮，则会调用该对象的脚本（如果存在）中的 OnMouseDown 函数。
- ## 物理事件
  物理引擎将通过调用该对象的脚本上的事件函数来报告对象的碰撞情况。在进行接触、保持接触和中断接触时，将调用 [OnCollisionEnter](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnCollisionEnter.html)、[OnCollisionStay](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnCollisionStay.html) 和 [OnCollisionExit](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnCollisionExit.html) 函数。对象的碰撞体配置为触发器（即，碰撞体只检测某物何时进入而不进行物理反应）时，将调用相应的 [OnTriggerEnter](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnTriggerEnter.html)、[OnTriggerStay](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnTriggerStay.html) 和 [OnTriggerExit](https://docs.unity3d.com/cn/current/ScriptReference/MonoBehaviour.OnTriggerExit.html) 函数。如果在物理更新期间检测到多次接触，可能连续多次调用这些函数，因此会将一个参数传递给函数，从而提供碰撞的详细信息（位置、进入对象标识等）。
  ```
  void OnCollisionEnter(otherObj: Collision) {
    if (otherObj.tag == "Arrow") {
        ApplyDamage(10);
    }
  }
  ```