alias:: MacOS 路径

- 在 macOS 中，路径用于指定文件系统中文件和目录的位置。理解 macOS 中的路径可以帮助你更有效地通过 Finder、终端或编程方式访问和管理文件。以下是几种常见的路径类型以及如何使用它们的说明：
- ### 绝对路径
  绝对路径从根目录（`/`）开始，提供从根目录到特定文件或目录的完整序列。例如：
	- `/Users/username/Documents/report.docx`
	- `/Applications/Safari.app`
- ### 相对路径
  相对路径与当前工作目录有关，不从根目录开始。例如，如果你的当前目录是 `/Users/username/Documents`，并且你想访问同一目录下的 `Photos` 文件夹中的 `image.jpg`，你可以使用相对路径：
	- `Photos/image.jpg`
- ### 家目录简写
  在 macOS 终端中，你可以使用波浪号（`~`）作为家目录（即 `/Users/你的用户名`）的简写。这使得路径更加简洁。例如：
	- `~/Documents/report.docx` 相当于 `/Users/username/Documents/report.docx`
- ### 路径分隔符
  macOS 使用正斜杠（`/`）作为路径分隔符来区分路径中的各个部分。这一点与 Windows 系统不同，Windows 使用反斜杠（`\`）。
- ### 访问外部设备和网络位置
  当你连接外部存储设备（如 USB 驱动器）或访问网络位置时，这些通常挂载在 `/Volumes` 目录下。例如：
	- `/Volumes/MyExternalDrive/photos.jpg`
	- `/Volumes/NetworkShare/project.docx`
- ### 使用路径
  在 macOS 的 Finder 中，你通常不需要手动输入路径，但在使用终端或开发相关应用时，正确的路径指定是必须的。终端中可以使用命令如 `cd`（更改目录）和 `ls`（列出目录内容）来浏览文件系统。
- 了解和使用这些路径规则将帮助你更有效地在 macOS 系统中导航和管理文件。
  <!--Converted by ToLogseq-->
- ### 特殊目录名称
  在 Unix 和类 Unix 操作系统中（包括 macOS），`.`、`..` 和 `...` 是特殊的目录名称，用于表示当前目录结构中的特定位置。这里是每个符号的详细解释：
- ### 1. `.`
  单个点符号 `.` 代表当前工作目录。在命令行中使用时，它可以引用当前用户正在浏览的目录。例如，如果你正在 `/Users/username/Documents` 目录中，`./` 就指的是这个目录。
- ### 2. `..`
  两个点符号 `..` 代表当前目录的父目录。这是一种快速访问当前目录上一级的方式。继续上面的例子，如果你在 `/Users/username/Documents`，那么 `../` 将引用 `/Users/username` 目录。
- ### 转义字符
  路径中空格前需要加`\`
-