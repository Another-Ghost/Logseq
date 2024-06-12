- `yarn` 是一个快速、可靠、安全的依赖管理工具。以下是一些基本的 `yarn` 命令：
	- 安装 `yarn`：
	  logseq.order-list-type:: number
	  ```bash
	  npm install -g yarn
	  ```
	- 创建一个新的项目：
	  logseq.order-list-type:: number
	  ```bash
	  yarn init
	  ```
	- 添加一个依赖：
	  logseq.order-list-type:: number
	  ```bash
	  yarn add [package]
	  # 或者添加为开发依赖
	  yarn add [package] --dev
	  ```
	- 升级一个依赖：
	  logseq.order-list-type:: number
	  ```bash
	  yarn upgrade [package]
	  # 或者升级到特定版本
	  yarn upgrade [package]@[version]
	  ```
	- 删除一个依赖：
	  logseq.order-list-type:: number
	  ```bash
	  yarn remove [package]
	  ```
	- 安装所有的依赖：
	  logseq.order-list-type:: number
	  ```bash
	  yarn
	  # 或者
	  yarn install
	  ```
- 这只是 `yarn` 的一些基本用法，`yarn` 还有许多其他的命令和选项可以使用。
  <!--Converted by ToLogseq-->
- ## yarn 和 [[npm]]
	- `npm` 和 `yarn` 都是 [[JavaScript]] 项目的包管理工具，它们有许多相似之处，但也有一些关键的区别。
		- **性能**：在初次安装项目依赖时，`yarn` 通常比 `npm` 更快，因为 `yarn` 并行执行操作，而 `npm` 则是串行执行。
		  logseq.order-list-type:: number
		- **yarn.lock vs [[package-lock.json]]**：`yarn` 和 `npm` 都有锁定文件，确保依赖的一致性。`yarn` 使用 `yarn.lock`，而 `npm` 使用 `package-lock.json`。
		  logseq.order-list-type:: number
		- **安全性**：`yarn` 在添加新的依赖时会自动运行其安全检查，而 `npm` 需要手动运行 `npm audit`。
		  logseq.order-list-type:: number
		- **工作区**：`yarn` 支持工作区，这使得在一个仓库中管理和链接多个包变得更加容易。`npm` 在 v7.0+ 也开始支持工作区。
		  logseq.order-list-type:: number
	- 以下是一些基本的 `npm` 和 `yarn` 命令的对比：
		- 安装所有依赖：
		  ```bash
		  npm install
		  yarn
		  ```
		- 安装一个包：
		  ```bash
		  npm install [package]
		  yarn add [package]
		  ```
		- 安装一个开发依赖：
		  ```bash
		  npm install --save-dev [package]
		  yarn add --dev [package]
		  ```
		- 删除一个包：
		  ```bash
		  npm uninstall [package]
		  yarn remove [package]
		  ```
		- 更新一个包：
		  ```bash
		  npm update [package]
		  yarn upgrade [package]
		  ```
		- 运行一个脚本：
		  ```bash
		  npm run [script]
		  yarn [script]
		  ```
	- 这只是 `npm` 和 `yarn` 的一些基本对比，它们都有许多其他的命令和特性。
	  <!--Converted by ToLogseq-->