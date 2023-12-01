- `git reset --mixed <commit>`
	- 当你执行 `git reset --mixed <commit>` 时，Git 会将当前分支的 HEAD 重置到指定的 `<commit>`。
	- 这个命令会影响暂存区和 HEAD，但不会影响工作目录。
	- 在执行这个命令之后，所有自 `<commit>` 以来的提交所包含的更改将从暂存区移除，但这些更改仍然会保留在工作目录中。这意味着这些更改现在处于未暂存（unstaged）的状态。
	- #+BEGIN_PINNED
	  这个命令在你想要撤销一些提交，但又想保留这些更改以便进一步检查和修改时非常有用。它提供了一种方式来重新调整你的代码提交历史，同时保持你的工作进度。
	  #+END_PINNED
- `git reset --hard`
	- git reset --hard HEAD^ 回退到上个版本。
	  git reset --hard HEAD~n 回退到前n次提交之前，若n=3，则可以回退到3次提交之前。
	  git reset --hard commit_sha 回滚到指定commit的sha码，推荐使用这种方式。