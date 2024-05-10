alias:: Extensible Data Notation

- EDN（Extensible Data Notation）是一种基于文本的、灵活的数据表示格式。它最初由Clojure社区开发，但因其简洁和多功能性逐渐在其他领域得到使用。EDN与JSON、YAML等相似，但具有独特的特征，使其成为描述和传输数据的理想选择。
- ## 基本语法
- EDN (Extensible Data Notation) 是一种简单而强大的数据描述语言，最初由 Clojure 社区开发。它类似于 JSON 和 YAML，但具有更丰富的特性，包括支持更广泛的数据结构、注释、关键字等。EDN 常用于配置文件、数据传输、数据持久化等。
- ### 基本语法
  EDN 的基本语法包括以下元素：
	- **原始数据类型**：
	  logseq.order-list-type:: number
		- **字符串**：用双引号包围，例如 `"hello world"`。支持转义字符，如 `\"`, `\\`, `\n`, `\t` 等。
		- **数字**：支持整数和浮点数，例如 `42`, `3.14`。
		- **布尔值**：`true`, `false`。
		- **nil**：表示空值或无值。
	- **数据结构**：
	  logseq.order-list-type:: number
		- **列表**：用圆括号包围，例如 `(1 2 3)`。在 Clojure 中，列表通常用于表示函数调用。
		- **向量**：用方括号包围，例如 `[1 2 3]`。向量是有序的集合。
		- **映射**：用花括号包围，例如 `{:a 1, :b 2}`。映射由键值对组成。
		- **集合**：用大括号包围，例如 `#{1 2 3}`。集合中的元素是无序且唯一的。
	- **关键字和符号**：
	  logseq.order-list-type:: number
		- **关键字**：以冒号开头，例如 `:keyword`。关键字用于标记和引用数据。
		- **符号**：用于表示变量或表达式，例如 `'symbol`。
	- **注释**：
	  logseq.order-list-type:: number
		- EDN 支持单行注释，以分号（`;`）开头，整行都是注释内容。
- ### 示例
  以下是一个包含各种数据结构的 EDN 示例：
  ```edn
  {
  :name "Alice"
  :age 28
  :hobbies ["reading" "skiing" "baking"]
  :is-active true
  :address {
    :street "123 Main St"
    :city "Springfield"
    :postal-code 12345
  }
  ; 这是一个注释
  }
  ```
- ### 扩展与自定义
  EDN 支持自定义标签，允许扩展数据类型。这意味着可以在 EDN 中添加自定义数据类型，并通过解析器进行处理。
- ### EDN的主要特点
	- **灵活数据结构**：EDN支持常见的数据结构，如列表、向量、集合和映射（键值对）。
	- **关键字和符号**：EDN提供了关键字（如 `:keyword`）和符号（如 `'symbol`），用于标记和引用数据。
	- **注释**：EDN支持单行注释，使用分号（`;`）开头。相比之下，JSON不支持注释。
	- **可扩展性**：EDN允许用户自定义标签和数据类型，这意味着你可以在EDN中表示复杂的数据结构。
- ### EDN与JSON、YAML的比较
	- **与JSON相比**：EDN支持更复杂的数据结构，如集合和符号。它还支持注释，而JSON不支持。
	- **与YAML相比**：EDN具有更严格的语法，更不容易出错。YAML的自由格式容易导致解析错误。
- ### EDN的应用
	- **配置文件**：EDN可以用来存储应用程序的配置。
	- **数据交换**：EDN可以用于不同系统之间传输数据。
	- **数据存储**：由于EDN的灵活性和可读性，它也适合用于持久化数据。
- ### 解析和生成EDN
  在Clojure中，可以使用 `clojure.edn/read` 来解析EDN。在其他编程语言中，有许多第三方库可以处理EDN，例如Python的 `edn_format`、JavaScript的 `jsedn` 等。
-
- ### EDN 的解析和生成
  Clojure 内置了处理 EDN 的函数，其他语言也有第三方库来解析和生成 EDN。例如，Python 的 `edn_format`、JavaScript 的 `jsedn` 等。
-