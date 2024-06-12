- 使用以下命令将你的分支推送到 GitHub：
- ```
  git push -u origin branch_name
  ```
- 这里，`branch_name` 是你想要推送的分支名，`origin` 是远程仓库的默认名称（除非你在添加远程仓库时指定了其他名称）。
- `git push -u origin master` 是一个 Git 命令，用于将你的更改推送到远程仓库。这个命令可以分解为以下几个部分：
- `-u`：这是 `git push` 命令的一个选项，也可以写作 `--set-upstream`。这个选项会设置追踪信息，以便在未来的 Git 操作中，如 `git pull` 或 `git push` 时，不需要再指定远程仓库和分支。
- `origin`：这是你的远程仓库的名称。在大多数情况下，`origin` 是默认的远程仓库名称。
- `branch_name`：这是你要推送的分支名称。在大多数情况下，`main`/`master` 是默认的主分支名称。