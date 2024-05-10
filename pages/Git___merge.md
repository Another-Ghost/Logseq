- 当你尝试合并两个分支，但是这两个分支在同一文件的同一位置有不同的更改时，就会发生冲突。Git 无法决定应该保留哪个更改，所以它需要你手动解决冲突。
- 如果你想手动合并你的分支，你可以按照以下步骤操作：
	- 首先，你需要获取远程仓库的最新版本。你可以使用 `git fetch` 命令来获取：
	  logseq.order-list-type:: number
	  ```bash
	   git fetch origin
	   ```
	- 然后，你可以使用 `git merge` 命令来合并远程仓库的 `main` 分支到你的当前分支：
	  logseq.order-list-type:: number
	  ```bash
	   git merge origin/main
	   ```
	  如果你的本地分支和远程分支有冲突，那么 `git merge` 命令将会停止，让你解决这些冲突。
	- 打开有冲突的文件，找到以下这样的区域：
	  logseq.order-list-type:: number
	  ```plaintext
	   <<<<<<< HEAD
	   (你的更改)
	   =======
	   (来自被合并分支的更改)
	   >>>>>>> origin/main
	   ```
		- ![image.png](../assets/image_1713883337971_0.png)
	- 删除 `<<<<<<< HEAD`，`=======` 和 `>>>>>>> origin/main` 这些行，然后决定保留哪个更改，或者你也可以合并这两个更改。
	  logseq.order-list-type:: number
	- 保存并关闭文件。
	  logseq.order-list-type:: number
	- 使用 `git add` 命令来标记冲突已经解决：
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number
	  ```bash
	   git add <解决了冲突的文件>
	   ```
	- 提交你的更改：
	  logseq.order-list-type:: number
	  ```bash
	   git commit
	   ```
	  这时，你会看到一个包含默认合并消息的编辑器。你可以保留这个消息，或者输入你自己的消息来解释这次合并。保存并关闭编辑器后，你的合并就完成了。