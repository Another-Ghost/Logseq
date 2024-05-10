- 在macOS中，文件系统的组织方式是分层结构，设计用来支持多用户使用和操作系统的安全性。以下是macOS的一些主要目录及其用途：
- ### 根目录 (`/`) 
  logseq.order-list-type:: number
  根目录是文件系统的最顶层，所有其他文件和文件夹都从这里开始。
- ### 应用程序 (`/Applications`) 
  logseq.order-list-type:: number
  这个目录用来存放安装的应用程序。用户可以通过Finder访问这个目录，以查看和运行安装的应用。
- ### 系统 (`/System`) 
  logseq.order-list-type:: number
  存放macOS操作系统文件的目录。这些文件对于系统的运行至关重要，通常不应被修改或删除。
- ### 库 (`/Library`, `~/Library`, `/System/Library`) 
  logseq.order-list-type:: number
  这些库文件夹包含了各种支持文件，如偏好设置、应用支持文件和插件等。
	- `/Library`：用于存放所有用户的系统级支持文件和应用程序支持文件。
	- `~/Library`：用于存放单个用户的个人设置和应用程序数据。
	- `/System/Library`：仅用于由macOS系统使用的文件。
- ### 用户 (`/Users`) 
  logseq.order-list-type:: number
  这个目录下包含了每个用户的个人文件夹，通常按照用户名命名。用户的桌面、文档、下载等文件夹都位于其个人文件夹内。
- ### 临时文件 (`/tmp`, `/var/tmp`) 
  logseq.order-list-type:: number
  用于存放临时文件，这些文件通常在重新启动后被清除。
- ### 变量数据 (`/var`) 
  logseq.order-list-type:: number
  存储系统运行时生成的信息，如日志文件。
- ### 二进制文件 (`/bin`, `/sbin`, `/usr/bin`, `/usr/sbin`) 
  logseq.order-list-type:: number
  这些目录包含系统命令和程序，它们是操作系统功能的一部分。
	- `/bin` 和 `/usr/bin`：存放标准命令。
	- `/sbin` 和 `/usr/sbin`：存放系统管理命令，通常由系统管理员使用。
- ### 本地文件 (`/usr/local`) 
  logseq.order-list-type:: number
  这是一个用于安装用户程序的地方，通常不会与系统提供的程序冲突。例如，通过Homebrew安装的程序通常位于`/usr/local/bin`。
- ### 设备和设备接口 (`/dev`) 
  logseq.order-list-type:: number
  包含设备和设备接口文件，用于系统与硬件的交互。
-