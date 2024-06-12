- `git checkout` 是一个 Git 命令，用于切换分支或恢复工作树文件。以下是一些基本的用法：
- 1. **切换分支**：如果你想要切换到一个已经存在的分支，你可以使用 `git checkout` 命令 followed by the name of the branch. 例如，如果你有一个名为 `feature` 的分支，你可以使用以下命令切换到这个分支：
- ```bash
  git checkout feature
  ```
- 2. **创建并切换到新的分支**：如果你想要创建一个新的分支并立即切换到这个分支，你可以使用 `-b` 参数 followed by the name of the new branch. 例如，如果你想要创建一个名为 `new-feature` 的分支，你可以使用以下命令：
- ```bash
  git checkout -b new-feature
  ```
- 3. **恢复文件**：`git checkout` 命令也可以用来恢复工作树的文件。例如，如果你修改了一个名为 `file.txt` 的文件，但你想要丢弃这些修改并恢复到最后一次提交的状态，你可以使用以下命令：
  ```bash
  git checkout -- file.txt
  ```
- 请注意，这将会丢弃 `file.txt` 文件的所有未提交的修改，这个操作是不可逆的。
- 这只是 `git checkout` 的一些基本用法，`git checkout` 还有许多其他的选项和特性。