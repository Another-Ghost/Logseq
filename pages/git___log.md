- `git log` 是一个 Git 命令，用于显示提交历史。它会按照时间顺序列出所有的提交，最近的提交在最上面。
- 基本的 `git log` 命令会显示每个提交的 SHA-1 校验和、作者、日期和提交信息：
- ```bash
  git log
  ```
- 你还可以使用一些选项来定制 `git log` 的输出。例如，`-n` 选项可以限制显示的提交数量：
- ```bash
  git log -n 3
  ```
- 上面的命令只会显示最近的三个提交。
- `--pretty` 选项可以改变 `git log` 的输出格式。例如，`--pretty=oneline` 会让每个提交只占一行：
- ```bash
  git log --pretty=oneline
  ```
- `--graph` 选项可以显示一个 ASCII 图形表示的分支和合并历史：
- ```bash
  git log --graph
  ```
- 这只是 `git log` 的一些基本用法，`git log` 还有许多其他的选项和特性。