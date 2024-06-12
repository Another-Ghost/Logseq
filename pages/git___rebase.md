- `git rebase` 是一个 Git 命令，用于将一系列的提交应用到另一个基点上。它是一种改变提交历史的方式。
- 以下是 `git rebase` 的一些基本用法：
- 1. **基本的 rebase**：如果你在 `feature` 分支上工作，然后 `master` 分支有了新的提交，你可能想要将这些新的提交应用到你的 `feature` 分支上。你可以先切换到 `feature` 分支，然后运行 `git rebase master`：
- ```bash
  git checkout feature
  git rebase master
  ```
- 这将会将 `feature` 分支上的提交暂时移除，将 `master` 分支上的新的提交应用到 `feature` 分支，然后再将 `feature` 分支上的提交应用回来。
- 2. **交互式 rebase**：`git rebase` 命令的 `-i` 或 `--interactive` 选项可以启动交互式 rebase。这允许你修改提交历史，例如合并、修改、重新排序或删除提交。例如，`git rebase -i HEAD~3` 将会启动一个交互式 rebase，让你修改最近的三个提交。
- ```bash
  git rebase -i HEAD~3
  ```
- 请注意，`git rebase` 会改变提交历史，所以在公共的分支上使用 `git rebase` 需要特别小心。如果你不确定，你可以使用 `git merge` 来合并改动，这不会改变提交历史。
- ``` bash
  git rebase PuerTestDemo
  Successfully rebased and updated refs/heads/master.
  ```
-