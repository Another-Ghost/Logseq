alias:: 分支

- 在 Git 中，分支是一个指向提交对象的可变指针。每次你提交代码，Git 都会创建一个新的提交对象，并将当前分支的指针移动到这个新的提交对象。
- 分支使得并行开发成为可能。你可以在一个分支上进行新功能的开发，同时在另一个分支上进行 bug 修复或者稳定版本的维护。当新功能开发完成后，你可以将这个分支合并到主分支，这样主分支就包含了新功能的所有代码。
- Git 的分支非常轻量级，创建和切换分支非常快速。这使得在多个分支之间频繁切换成为可能，可以根据需要进行不同的任务。
- 在 Git 中，有一个特殊的分支叫做 `HEAD`。它是一个指向你当前正在工作的最后一次提交的指针。当你切换分支时，`HEAD` 会移动到新分支的最后一次提交。
- `origin` 是默认的远程仓库名称，`origin/main` 或 `origin/master` 通常指的是远程仓库的主分支。当你从远程仓库拉取代码时，Git 会更新 `origin/main` 或 `origin/master` 指向的提交。
- ## 命令
	- 在 Git 中，你可以使用 `git branch` 命令来查看、创建和删除分支。
	- 查看分支：你可以使用 `git branch` 命令来查看你的本地仓库的所有分支。当前活动的分支前面会有一个 `*` 标记。
	  
	  ```bash
	  git branch
	  ```
		- ### 查看远程仓库
			- 在 Git 中，你可以使用 `git branch -r` 或 `git branch -a` 命令来查看远程仓库的分支列表。
			- `git branch -r`：这个命令会显示所有远程仓库的分支。
			- `git branch -a`：这个命令会显示所有本地和远程仓库的分支。
			  在运行这些命令之前，你可能需要先使用 `git fetch` 命令来获取远程仓库的最新信息。
			  ```bash
			  git fetch origin
			  git branch -r
			  ```
			  
			  这样，你就可以看到远程仓库的所有分支列表了。
	- 创建分支：你可以使用 `git branch <branch-name>` 命令来创建一个新的分支，其中 `<branch-name>` 是你想要的分支名称。
	  
	  ```bash
	  git branch new-branch
	  ```
	- 切换分支：你可以使用 `git checkout <branch-name>` 命令来切换到一个已存在的分支，其中 `<branch-name>` 是你想要切换到的分支名称。
	  
	  ```bash
	  git checkout new-branch
	  ```
	- 删除分支：你可以使用 `git branch -d <branch-name>` 命令来删除一个已存在的分支，其中 `<branch-name>` 是你想要删除的分支名称。
	  
	  ```bash
	  git branch -d old-branch
	  ```
	  
	  这些是 `git branch` 命令的基本用法。你还可以使用其他选项来进行更复杂的操作。
- 如果你想创建一个新的分支同时切换到新创建的分支的话，可以通过 `git checkout -b <your-branch-name>` 来实现。
- ```cpp
  git branch -D PuerTestDemo
  Deleted branch PuerTestDemo (was eaa69cb).
  ```
-