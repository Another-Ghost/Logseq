- `.plist` 文件是 macOS 和 iOS 中使用的^^属性列表文件^^格式。这种文件格式用于存储^^配置信息、偏好设置、应用程序的元数据^^等。`.plist` 文件使用 XML 或二进制格式编码，并且通常以 XML 格式的文件出现，可以用文本编辑器打开和编辑。
- 属性列表文件通常包含键-值对的数据结构，类似于 JSON 或字典（dictionary）数据类型。每个键都有一个相关联的值，可以是字符串、数字、布尔值、日期等。
- `.plist` 文件的一些常见用途包括：
	- **应用程序配置**: 许多 macOS 和 iOS 应用程序使用 `.plist` 文件来存储应用程序的配置信息，例如窗口大小、位置、默认设置等。
	  logseq.order-list-type:: number
	- **偏好设置**: 用户的偏好设置通常也存储在 `.plist` 文件中，例如应用程序的首选语言、主题、字体大小等。
	  logseq.order-list-type:: number
	- **Bundle 信息**: 在 macOS 和 iOS 中，应用程序的 Bundle 中包含一个或多个 `.plist` 文件，用于指定应用程序的版本号、标识符、图标文件名等元数据。
	  logseq.order-list-type:: number
	- **系统设置**: macOS 中的一些系统设置也存储在 `.plist` 文件中，例如网络设置、系统偏好设置等。
	  logseq.order-list-type:: number
- `.plist` 文件可以由开发人员手动创建和编辑，也可以由应用程序动态生成和修改。在 macOS 和 iOS 中，开发人员通常使用 Foundation 框架提供的 API 来读取和写入 `.plist` 文件中的数据。