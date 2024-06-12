## 显示 [[隐藏文件]]
	- 在 macOS 中，你可以使用以下的命令在 Finder 中显示隐藏文件：
	- ```bash
	  defaults write com.apple.finder AppleShowAllFiles YES
	  ```
	- 然后，你需要重启 Finder 以使这个设置生效：
	- ```bash
	  killall Finder
	  ```
	- 如果你想要在 Finder 中隐藏这些文件，你可以使用以下的命令：
	- ```bash
	  defaults write com.apple.finder AppleShowAllFiles NO
	  killall Finder
	  ```
	- 在终端中，你可以使用 `ls` 命令的 `-a` 或 `-A` 选项来显示隐藏文件。`-a` 选项会显示所有文件，包括 `.` 和 `..`，而 `-A` 选项不会显示 `.` 和 `..`：
	- ```bash
	  ls -a
	  ```
	- 或者：
	- ```bash
	  ls -A
	  ```