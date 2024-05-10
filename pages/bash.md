alias:: bourne agian shell

- Bash（Bourne Again SHell）是一种广泛使用的 Unix shell 和命令语言，由 Brian Fox 为 GNU 项目编写并在 1989 年首次发布。它是 Bourne Shell 的替代品，包含了 Bourne Shell 的所有功能，并加入了一些新的功能来增强其可用性和可扩展性。Bash 是大多数 Linux 发行版以及 macOS 的默认 [[shell]] ，是 shell 的主要版本。
- ### 主要特性
	- **命令行编辑**：Bash 提供了交互式命令行编辑、命令历史回溯和自动补全功能。
	  logseq.order-list-type:: number
	- **Shell 脚本编程**：Bash 支持复杂的 shell 脚本编程，包括条件语句、循环、函数、变量和数组等。
	  logseq.order-list-type:: number
	- **作业控制**：Bash 支持作业控制，可以暂停（挂起）和恢复（继续）执行的进程。
	  logseq.order-list-type:: number
	- **命令别名**：用户可以为经常使用的命令或命令序列定义别名，简化命令输入。
	  logseq.order-list-type:: number
	- **管道和重定向**：Bash 支持通过管道（|）将一个命令的输出作为另一个命令的输入，并支持输入/输出重定向。
	  logseq.order-list-type:: number
- ### Bash 脚本基础
  Bash 脚本是一种由多个命令组成的脚本文件，可以被 Bash 执行。一个基本的 Bash 脚本示例如下：
  ```bash
  #!/bin/bash
  # 这是一个注释
  echo "Hello, world!"  # 打印 Hello, world!
  
  # 变量
  name="World"
  echo "Hello, $name!"
  
  # 条件语句
  if [ $name == "World" ]; then
    echo "The name is World."
  else
    echo "The name is not World."
  fi
  
  # 循环
  for i in {1..5}
  do
   echo "Looping ... number $i"
  done
  ```
- 在这个脚本中，包括了打印输出、使用变量、简单的 if 条件判断以及 for 循环。
- ### 执行 Bash 脚本
  要运行 Bash 脚本，你需要做以下步骤：
	- 创建一个文本文件，并将上面的脚本内容保存进去，假设文件名为 `script.sh`。
	  logseq.order-list-type:: number
	- 通过命令行赋予该脚本执行权限：
	  logseq.order-list-type:: number```bash
	  chmod +x script.sh
	  ```
	  - 在命令行中执行脚本：
	  logseq.order-list-type:: number```bash
	  ./script.sh
	  ```
- ### 使用 Bash 的提示
	- **保持脚本的可移植性**：尽量使用 POSIX 标准的命令和结构，这样脚本就可以在其他兼容 POSIX 的 shell 中运行。
	- **注意安全性**：脚本中避免执行未经验证的输入，特别是在以 root 权限运行脚本时。
	- **利用社区资源**：Bash 的社区非常活跃，许多问题和高级用法可以通过网络资源找到答案。
- Bash 是一个功能强大的工具，无论是用于简单的日常任务还是复杂的系统管理，都是非常有用的资源。
  <!--Converted by ToLogseq-->