### 预设
预设是资源，可以用于在多个组件、资源或项目设置窗口中保存和应用相同的属性设置。您还可以使用预设在预设管理器中指定新组件的默认设置和资源的默认导入设置。预设管理器支持您添加到 Unity 编辑器的任何导入器、组件或可编写脚本的对象。
您只能在编辑器中应用预设。预设在运行时没有效果。您可以使用脚本在自己的 Monobehaviour、ScriptableObject 或 ScriptedImporter 类中支持预设。
- ### 保存和应用预设
  预设允许您将组件、资源或项目设置窗口的属性配置保存为预设资源。然后，您可以使用此预设资源将相同的设置应用于不同的组件、资源或项目设置窗口。
  例如，您可以编辑 Rigidbody 组件的属性，将这些设置保存为预设资源，然后将该预设资源应用于其他 GameObjects 中的 Rigidbody 组件。其他 GameObjects 中的组件不受影响；预设仅将其设置应用于 Rigidbody 组件。
  您可以将预设存储在项目的 Assets 文件夹中。使用 Project 窗口查看并在 Inspector 中选择预设以进行编辑。
	- #### 在 Project 窗口中组织在 Presets 子文件夹中的预设资源的示例
- ### 将属性设置保存为预设
  要将属性设置保存为预设资源，请按照以下说明进行操作。您可以在编辑模式或播放模式下保存属性设置。
	- 选择要重复使用设置的 GameObject、资源导入设置或项目设置窗口。选择后，它会显示在 Inspector 窗口中。
	  logseq.order-list-type:: number
	- 在 Inspector 窗口中，配置要保存的属性。
	  logseq.order-list-type:: number
	- 点击 Inspector 窗口右上角的预设选择器（滑块图标）。
	  logseq.order-list-type:: number
	- 在“选择预设”窗口中，点击“保存当前到...”
	  logseq.order-list-type:: number
	- 出现文件保存对话框。
	  logseq.order-list-type:: number
	- 选择新预设的位置，输入其名称，然后点击“保存”。
	  logseq.order-list-type:: number
- ### 从预设应用设置
  有两种方法可以应用预设：通过“选择预设”窗口，或者对于组件预设，您还可以从 Project 窗口将预设拖放到包含该组件的 GameObject 上。
  注意：应用预设会将属性从预设复制到项目中。它不会将预设链接到项目中。您对
- 已应用预设的项目进行的更改不会影响已应用预设的项目。
	- #### 通过“选择预设”窗口应用预设：
	- 对于您要应用预设的 GameObject 或资源，选择它们，使它们显示在 Inspector 窗口中。对于要应用预设的项目设置，在项目设置窗口中打开它们。
	  logseq.order-list-type:: number
	- 在 Inspector 中，点击预设选择器（滑块图标）。
	  logseq.order-list-type:: number
	- 在“选择预设”窗口中，搜索并选择要应用的预设。
	  logseq.order-list-type:: number
	- Unity 将此预设应用于组件、资源或项目设置窗口。
	  logseq.order-list-type:: number
	- 关闭“选择预设”窗口。
	  logseq.order-list-type:: number
	- #### 通过拖放方式应用组件预设：
	  Unity 的行为取决于 GameObject 的状态：
	- 如果将预设拖放到 Hierarchy 窗口中的现有 GameObject 上，Unity 将添加一个新组件，并从预设中复制属性。
	- 如果将预设拖放到 Hierarchy 窗口中的空白区域，Unity 将创建一个新的空 GameObject，并添加一个带有从预设中复制的属性的组件。
	- 如果将预设拖放到 Inspector 窗口中的现有组件标题上，Unity 将从预设中复制属性。
	- 如果将预设拖放到 Inspector 窗口中的空白区域，Unity 将添加一个新组件，并从预设中复制属性。
- ### 应用部分预设
  您可以选择仅应用预设中的某些属性，而排除其他属性。要执行此操作：
	- 在 Project 窗口中选择您的预设。
	  logseq.order-list-type:: number
	- 在 Inspector 中，右键点击一个属性并选择“排除属性”。窗口会在排除的属性旁边显示一条红色水平线。
	  logseq.order-list-type:: number
	- 将预设应用于目标组件、资源或项目设置。
	  logseq.order-list-type:: number
	  注意：要在预设中选择全部或清除所有复选框，请选择“更多项目”菜单（⋮）或右键点击预设名称，然后选择“包括所有属性”或“排除所有属性”。如果需要，您仍然可以调整单个属性。
	  您还可以对预设设置为组件和资源导入器的默认配置使用“排除”选项。有关如何执行此操作的更多详细信息，请参阅预设管理器。
- ### 编辑预设
  要编辑预设资源，请从 Project 窗口中选择它，并在 Inspector 窗口中查看它。
  注意：当您更改预设中的属性时，您的更改不会影响已经应用该预设的项目。例如，如果您将 Rigidbody 组件的预设应用于一个 GameObject，然后编辑该预设，则 Rigidbody 组件中的设置不会更改。
	- #### 在 Inspector 窗口中编辑预设的示例
- ### 使用脚本根据文件夹导入资源并应用预设
  您可以使用脚本根据资源在 Project 窗口中的位置将预设应用于资源。
- ### 导出预设资源
  使用预设可以简化团队的工作流程。您甚至可以使用预设为项目设置窗口指定设置，包括预设本身的设置。使用此功能可以配置项目，然后将其导出为自定义资源包。您的团队成员可以将此资源包导入他们的项目中。
	- 在 Project 窗口中，选择要导出的预设。
	  logseq.order-list-type:: number
	- 在 Unity 菜单中，转到 Assets > Export Package，或在 Project 窗口中右键点击并选择 Export Package。
	  logseq.order-list-type:: number
	- 导出包窗口显示要导出的项目。
	  logseq.order-list-type:: number
	- 如果您的预设包含要包含在包中的资源引用，请启用“包含依赖项”。
	  logseq.order-list-type:: number
	- 点击“导出”。
	  logseq.order-list-type:: number
	- 选择要存储包的位置，输入文件名，然后点击“保存”。Unity 将包保存为 .unitypackage 文件。
	  logseq.order-list-type:: number
- ### 使用预设进行动画状态节点的过渡
  您可以为动画状态节点保存和应用预设。但是，预设中的过渡在预设和您应用预设的节点之间共享。例如，您将预设应用于 Animator 窗口中的两个不同节点。在 Inspector 窗口中，您编辑第一个节点中某个过渡的设置。您的更改也会出现在另一个节点和预设中。
  <!--Converted by ToLogseq-->
-