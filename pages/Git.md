# 基础概念
- [[HEAD]]: 在 Git 中，HEAD 指的是[[当前分支]]的 *最新[[提交]]*。
- [[暂存区]]: 这是 Git 中的一个区域，用于**存放准备下一次提交的文件**。
- [[工作目录]]: 这是**用户正在工作的目录**，包含了项目的所有文件和文件夹。
- # 常用命令
	- ## Config
		- 查看用户名和邮箱地址：
		  ```
		  $ git config user.name
		  - $ git config user.email
		  ```
		- 修改用户名和邮箱地址：
		  ```
		  $ git config --global user.name "username"
		  - $ git config --global user.email "email"
		  ```
		- 查看当前配置
		  `git config --list`
	- # diff
		- 查看冲突文件。
	-
- git fetch从远程分支拉取代码。
- fetch常结合merge一起用，git fetch + git merge == git pull
- 一般要用git fetch+git merge，因为git pull会将代码直接合并，造成冲突等无法知道，fetch代码下来要git
  diff orgin/xx来看一下差异然后再合并。
	- 链接：https://www.jianshu.com/p/a5c4d2f99807
-
- 创建新分支：git branch branchName
- 切换到新分支：git checkout branchName
-
- git clone git@github.com:Another-Ghost/LogseqNote.git
-
- `git add <filename>`
  `git add *`
- `git commit -m "代码提交信息"`
- `git push origin master`
-
- # Error
	- [A lock file already exists in the repository](https://stackoverflow.com/questions/66449211/a-lock-file-already-exists-in-the-repository-which-blocks-this-operation-from-c)
	  logseq.order-list-type:: number