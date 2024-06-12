- 在使用虚幻引擎时，选择正确的IDE对于高效的编程工作至关重要。JetBrains提供的Rider IDE有两个与虚幻引擎相关的版本：Rider for Unreal Engine（常简称为Rider）和RiderLink（与虚幻引擎项目相关联的插件，有时称为Rider Uproject）。下面是这两者的区别：
- ### Rider for Unreal Engine
  Rider for Unreal Engine是JetBrains开发的一款针对虚幻引擎项目优化的IDE。这个版本的Rider包含了许多专门为虚幻引擎设计的功能，如：
	- **增强的C++支持**：包括对虚幻引擎API的深度集成和代码智能提示。
	- **虚幻引擎专用工作流**：如蓝图调试和反射系统支持。
	- **高效的代码导航和搜索**：针对虚幻引擎项目的代码结构优化。
	- **直接集成虚幻编辑器的功能**：可以直接从IDE启动和停止虚幻引擎编辑器。
- ### RiderLink (Rider Uproject)
  RiderLink不是一个独立的IDE，而是一个为Rider for Unreal Engine设计的插件，它允许Rider IDE与虚幻引擎的编辑器直接交互。这个插件是通过虚幻引擎的插件系统安装到虚幻引擎项目中的（即Uproject），具体包括：
	- **改进的调试体验**：允许从Rider IDE中直接启动和调试虚幻引擎项目。
	- **实时的代码同步**：编辑C++代码时，更改可以即时反映在虚幻引擎编辑器中。
	- **更强大的代码分析**：提供实时的代码质量检查和改进建议。
- 总的来说，Rider for Unreal Engine是一个完整的IDE，专为虚幻引擎开发者设计，而RiderLink是一个插件，用于增强Rider与虚幻引擎之间的集成和交互。如果你在使用Rider进行虚幻引擎开发，通常需要同时使用Rider IDE和RiderLink插件来获得最佳的开发体验。
  <!--Converted by ToLogseq-->
- Git pull
	- ![image.png](../assets/image_1715092612692_0.png)
- ## 搜索快捷键
	- 在JetBrains Rider中，快捷键可以大大提高你的开发效率。以下是一些与搜索相关的常用快捷键：
	- ### 搜索快捷键
		- **^^搜索任何内容^^（Search Everywhere）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Shift` + `Shift`
			- **macOS**: `⇧` + `⇧`（两次Shift）
			- 这个快捷键允许你快速搜索类、文件、符号、以及动作或设置。
		- **在路径中搜索（Find in Path）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `Shift` + `F`
			- **macOS**: `⌘` + `⇧` + `F`
			- 这个功能让你可以在整个项目或指定范围内搜索文本。
		- **查找类（Find Class）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `N`
			- **macOS**: `⌘` + `O`
			- 用于快速定位和打开类文件。
		- **查找文件（Find File）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `Shift` + `N`
			- **macOS**: `⌘` + `⇧` + `O`
			- 用于搜索并打开项目中的文件。
		- **查找符号（Find Symbol）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `Alt` + `Shift` + `N`
			- **macOS**: `⌘` + `⌥` + `⇧` + `O`
			- 用于搜索和导航到项目中的符号（如方法、变量等）。
		- **跳转到文件（Navigate to File）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `Shift` + `T`
			- **macOS**: `⌘` + `⇧` + `T`
			- 允许你通过文件名快速跳转到文件。
		- **^^最近的文件^^（Recent Files）**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `E`
			- **macOS**: `⌘` + `E`
			- 列出最近打开的文件，方便快速切换。
		- **查找和替换（Find and Replace）**：
		  logseq.order-list-type:: number
			- **查找**：
				- **Windows/Linux**: `Ctrl` + `F`
				- **macOS**: `⌘` + `F`
			- **^^替换^^**：
				- **Windows/Linux**: `Ctrl` + `R`
				- **macOS**: `⌘` + `R`
	- ### 如何查看和修改快捷键
	  你可以在Rider中查看和修改快捷键：
		- **打开设置**：
		  logseq.order-list-type:: number
			- **Windows/Linux**: `Ctrl` + `Alt` + `S`
			- **macOS**: `⌘` + `,`
		- **导航到键位映射（Keymap）**：
		  logseq.order-list-type:: number
			- 在设置窗口中，导航到 `Keymap` 部分。
		- **搜索和修改快捷键**：
		  logseq.order-list-type:: number
			- 在 `Keymap` 中，你可以搜索特定的动作并查看其当前的快捷键。你还可以双击某个动作并为其设置新的快捷键。
	- 通过熟练使用这些快捷键，你可以更高效地进行代码搜索和导航，提高开发效率。
	  <!--Converted by ToLogseq-->
- ## 查看继承层次
  在JetBrains Rider中，查看类的继承关系可以帮助你理解项目的结构和类之间的关系。Rider提供了多种工具和视图来查看类的继承层次。以下是一些查看类继承关系的常用方法：
- ### 使用继承层次视图（Hierarchy View）
	- **查看类型层次（Type Hierarchy）**：
	  logseq.order-list-type:: number
		- **快捷键**：
			- **Windows/Linux**: `Ctrl` + `H`
			- **macOS**: `⌃` + `H`
		- **使用方法**：将光标放在你感兴趣的类名上，然后按下上述快捷键。Rider会打开一个窗口，显示该类的继承层次，包括父类和子类。
	- **查看方法层次（Method Hierarchy）**：
	  logseq.order-list-type:: number
		- **快捷键**：
			- **Windows/Linux**: `Ctrl` + `Shift` + `H`
			- **macOS**: `⌃` + `⇧` + `H`
		- **使用方法**：将光标放在一个方法名上，然后按下上述快捷键。Rider会显示该方法在继承层次中的重写情况。
	- **^^查看调用层次（Call Hierarchy）^^**：
	  logseq.order-list-type:: number
		- **快捷键**：
			- **Windows/Linux**: `Ctrl` + `Alt` + `H`
			- **macOS**: `⌥` + `⌘` + `H`
		- **使用方法**：将光标放在方法名上，按下上述快捷键。Rider会显示该方法的调用关系，包括调用者和被调用者。
- ### 使用结构工具窗口（Structure Tool Window）
	- **打开结构工具窗口**：
		- **快捷键**：
			- **Windows/Linux**: `Alt` + `7`
			- **macOS**: `⌘` + `7`
		- **使用方法**：在结构工具窗口中，你可以查看当前文件的结构，包括类和成员。虽然这个窗口不会直接显示继承关系，但它有助于你快速浏览和导航代码。
- ### 使用导航功能（Navigate Functionality）
	- **快速导航到父类/接口（Navigate to Super Class/Interface）**：
	  logseq.order-list-type:: number
		- **快捷键**：
			- **Windows/Linux**: `Ctrl` + `U`
			- **macOS**: `⌘` + `U`
		- **使用方法**：将光标放在类名上，按下快捷键，Rider会跳转到该类的父类或接口定义。
	- **快速导航到实现（Navigate to Implementations）**：
	  logseq.order-list-type:: number
		- **快捷键**：
			- **Windows/Linux**: `Ctrl` + `Alt` + `B`
			- **macOS**: `⌥` + `⌘` + `B`
		- **使用方法**：将光标放在类名或方法名上，按下快捷键，Rider会显示所有实现该类或方法的位置。
- ### 使用代码检查功能（Code Inspection）
	- **查看类的继承关系和使用情况**：
		- 你可以使用Rider的代码检查功能，右键点击类名，选择 `Find Usages` 或 `Show Usage`，这会显示该类在项目中的所有引用和使用情况，有助于你理解其继承关系和应用场景。
- 通过这些工具和视图，Rider可以帮助你全面了解项目中类的继承关系和结构，使你在开发和维护代码时更加得心应手。
  <!--Converted by ToLogseq-->