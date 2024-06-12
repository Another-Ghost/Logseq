alias:: Extended Attribute, 扩展属性

- 在 macOS 中，`xattr` 命令用于管理文件的扩展属性（Extended Attributes）。扩展属性允许你为文件存储额外的元数据，这些元数据可以用于多种目的，例如标签、描述、安全信息等。
  以下是一些常用的 `xattr` 命令及其用法：
- ### 查看扩展属性
	- #### 列出文件的所有扩展属性
	  ```sh
	  xattr <filename>
	  ```
	  例如：
	  ```sh
	  xattr example.txt
	  ```
	- #### 查看扩展属性的详细信息
	  ```sh
	  xattr -l <filename>
	  ```
	  例如：
	  ```sh
	  xattr -l example.txt
	  ```
- ### 添加或修改扩展属性
  ```sh
  xattr -w <attribute_name> <attribute_value> <filename>
  ```
  例如：
  ```sh
  xattr -w com.example.description "This is a sample document." example.txt
  ```
- ### 读取扩展属性的值
  ```sh
  xattr -p <attribute_name> <filename>
  ```
  例如：
  ```sh
  xattr -p com.example.description example.txt
  ```
- ### 删除扩展属性
  ```sh
  xattr -d <attribute_name> <filename>
  ```
  例如：
  ```sh
  xattr -d com.example.description example.txt
  ```
- ### 示例操作
  假设你有一个文件 `document.txt`，你想要添加一些扩展属性并查看它们。
	- **查看文件的现有扩展属性**
	  logseq.order-list-type:: number
	  ```sh
	  xattr -l document.txt
	  ```
	  如果文件没有任何扩展属性，这个命令将没有输出。
	- **添加扩展属性**
	  logseq.order-list-type:: number
	  ```sh
	  xattr -w com.example.author "Jane Smith" document.txt
	  xattr -w com.example.description "This is a sample document." document.txt
	  ```
	- **列出文件的所有扩展属性**
	  logseq.order-list-type:: number
	  ```sh
	  xattr document.txt
	  ```
	  输出可能类似于：
	  ```
	  com.example.author
	  com.example.description
	  ```
	- **查看特定扩展属性的值**
	  logseq.order-list-type:: number
	  ```sh
	  xattr -p com.example.author document.txt
	  ```
	  输出：
	  ```
	  Jane Smith
	  ```
	- **删除扩展属性**
	  logseq.order-list-type:: number
	  ```sh
	  xattr -d com.example.author document.txt
	  ```
	  再次查看扩展属性：
	  ```sh
	  xattr document.txt
	  ```
	  你将看到 `com.example.author` 属性已被删除，只剩下 `com.example.description`。
- ### 使用扩展属性的注意事项
	- **安全性**：不要在扩展属性中存储敏感信息，因为这些信息可能会被其他用户或应用程序读取。
	  logseq.order-list-type:: number
	- **兼容性**：并不是所有文件系统或操作系统都支持扩展属性，因此在跨平台使用文件时要注意这一点。
	  logseq.order-list-type:: number
	- **备份**：某些备份工具可能不会备份扩展属性，确保你的备份解决方案支持它们。
	  logseq.order-list-type:: number
	  了解和使用 `xattr` 命令可以帮助你更好地管理文件的元数据，提高文件管理的灵活性和效率。
	  <!--Converted by ToLogseq-->