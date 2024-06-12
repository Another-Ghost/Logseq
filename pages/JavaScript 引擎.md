- JavaScript 引擎是一个解释和执行 JavaScript 代码的程序。它是现代网页浏览器的核心组件，也被用于其他类型的应用，如服务器端（Node.js）、移动应用和桌面应用中。JavaScript 引擎的主要任务是将 JavaScript 代码转换成机器可执行的指令，从而使得能够在用户设备上运行复杂的应用程序。
- ### 主要的 JavaScript 引擎包括：
	- **V8** - 开发者为 Google，V8 是 Chrome 浏览器和 Node.js 中使用的 JavaScript 引擎。它以高性能著称，特别是在执行速度和动态优化方面。
	  logseq.order-list-type:: number
	- **SpiderMonkey** - 开发者为 Mozilla，这是 Firefox 浏览器中使用的第一个 JavaScript 引擎。它也是众多其他项目的基础，如 GNOME Shell 和 PDF.js。
	  logseq.order-list-type:: number
	- **JavaScriptCore (Nitro)** - 开发者为 Apple，用于 Safari 浏览器。在苹果的产品中，如 macOS 和 iOS，广泛使用。
	  logseq.order-list-type:: number
	- **Chakra** - 由微软开发，最初用于 Internet Explorer，后来在 Microsoft Edge 浏览器中得到了扩展，不过新版 Edge 浏览器已经转向使用 V8 引擎。
	  logseq.order-list-type:: number
	- **Hermes** - 由 Facebook 开发，专为 [[React Native]] 应用优化。它旨在提高移动应用的性能和启动时间。
	  logseq.order-list-type:: number
- ### 工作原理：
- JavaScript 引擎通常包括以下几个核心部分：
	- **解析器**（Parser）：读取源代码，检查其语法是否正确，并将代码转换为解释器能理解的结构。
	- **解释器**（Interpreter）：将代码转换成字节码，逐行解释执行。
	- **即时编译器**（[[JIT]] Compiler）：将频繁执行的字节码编译成优化的机器代码，提高执行效率。
	- **垃圾回收器**（Garbage Collector）：自动管理内存，回收不再使用的内存空间，防止内存泄漏。
- JavaScript 引擎的优化和发展一直是提高浏览器性能的重要因素之一，它们使得网页和应用能够更快地加载和执行，从而提供更好的用户体验。
  <!--Converted by ToLogseq-->