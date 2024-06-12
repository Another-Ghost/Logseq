### [[sudo]]
	- `sudo` 是一个在 Unix 和类 Unix 系统中用来提升权限的命令
- ### [[chown]]
	- `chown` 是 "change owner" 的缩写，这是一个 Unix 和类 Unix 系统中的命令，用于更改文件或目录的^^所有者^^和^^所属组^^。
	- ``` bash
	  sudo chown -R libo:admin /Users/libo/.npm/
	  ```
	  这个命令是用来更改 `/Users/libo/.npm/` 目录及其子目录和文件的所有者的。`chown` 是用来更改文件或者目录所有者的命令。
	- 在这个命令中，`-R` 参数表示**递归**地更改目录及其子目录和文件的所有者，`libo:admin` 表示新的所有者和所属组，`/Users/libo/.npm/` 是要更改所有者的目录。
	- 所以，这个命令的意思是，以超级用户的权限，将 `/Users/libo/.npm/` 目录及其子目录和文件的所有者更改为 `libo`，所属组更改为 `admin`。
- ### [[rm]]
	- `rm` 是 Unix 和 Unix-like 操作系统（包括 macOS 和 Linux）中的一个命令，用于删除文件和目录。其基本用法如下：
	- 删除文件：
	  ```bash
	  rm filename
	  ```
	- 删除目录（需要使用 `-r` 或 `-R` 参数，表示^^递归删除^^）：
	  ```bash
	  rm -r directoryname
	  ```
	- 在使用 `rm` 命令时要特别小心，因为一旦文件被删除，就无法恢复。如果你想在删除文件或目录前进行确认，可以添加 `-i` 参数：
	  ```bash
	  rm -i filename
	  ```
	- 这将会在删除每个文件前提示你确认。
- ### [[whoami]]
	- `whoami` 是一个 Unix 和类 Unix 系统中的命令，用于打印当前有效的用户名。
	- ```bash
	  whoami
	  ```
- ### [[xattr]]
-