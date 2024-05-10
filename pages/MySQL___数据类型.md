- MySQL 是一个广泛使用的关系数据库管理系统，它支持多种数据类型，允许开发者根据具体需要来存储不同类型的数据。以下是 MySQL 支持的主要数据类型的简介：
- ### 数字数据类型
	- **整数类型**：
	  logseq.order-list-type:: number
		- `TINYINT`：非常小的整数，占用 1 字节空间，范围从 -128 到 127。
		- `SMALLINT`：较小的整数，占用 2 字节空间，范围从 -32768 到 32767。
		- `MEDIUMINT`：中等大小的整数，占用 3 字节空间，范围从 -8388608 到 8388607。
		- `INT` 或 `INTEGER`：标准整数，占用 4 字节空间，范围从 -2147483648 到 2147483647。
		- `BIGINT`：较大的整数，占用 8 字节空间，范围从 -2^63 到 2^63-1。
	- **定点数和浮点数**：
	  logseq.order-list-type:: number
		- `FLOAT`：单精度浮点数。
		- `DOUBLE`：双精度浮点数。
		- `DECIMAL`：存储为字符串的定点数，适用于存储精确的小数，如金融数据。
- ### 字符串数据类型
	- **字符类型**：
	  logseq.order-list-type:: number
		- `CHAR`：固定长度字符串，最多可存储 255 个字符。
		- `VARCHAR`：可变长度字符串，最多可存储 65535 个字符。
	- **文本类型**：
	  logseq.order-list-type:: number
		- `TINYTEXT`：非常小的文本，最多可存储 255 个字符。
		- `TEXT`：普通文本，最多可存储 65535 个字符。
		- `MEDIUMTEXT`：中等长度文本，最多可存储 16777215 个字符。
		- `LONGTEXT`：最大长度文本，最多可存储 4294967295 个字符。
- ### 二进制数据类型
	- **二进制类型**：
	  logseq.order-list-type:: number
		- `BINARY`：固定长度二进制字符串。
		- `VARBINARY`：可变长度二进制字符串。
	- **Blob 类型**：
	  logseq.order-list-type:: number
		- `TINYBLOB`：非常小的 BLOB (Binary Large Object)。
		- `BLOB`：普通大小的 BLOB。
		- `MEDIUMBLOB`：中等大小的 BLOB。
		- `LONGBLOB`：最大大小的 BLOB。
- ### 日期和时间数据类型
	- **日期类型**：
	  logseq.order-list-type:: number
		- `DATE`：日期，格式为 YYYY-MM-DD。
		- `DATETIME`：日期和时间的组合，格式为 YYYY-MM-DD HH:MM:SS。
		- `TIMESTAMP`：时间戳，显示从 Unix 纪元（1970 年 1 月 1 日）到现在的秒数，有时区支持。
		- `TIME`：时间，格式为 HH:MM:SS。
		- `YEAR`：年份，2 位或 4 位格式。
- ### 枚举和集合数据类型
	- **ENUM**：
	  logseq.order-list-type:: number
		- 用于定义列的值必须从预设定的枚举列表中选择。
	- **SET**：
	  logseq.order-list-type:: number
		- 允许列包含零个或多个预设值。
- ### 布尔数据类型
	- `BOOLEAN`：布尔值，实际上是 `TINYINT(1)` 的别名，用 0 和 1 表示假和真。
- 这些数据类型使得 MySQL 可以灵活地处理各种数据，从简单的数值到复杂的文本文档或大型二进制对象。根据应用需求选择适当的数据类型是数据库设计中的一个关键步骤。
  <!--Converted by ToLogseq-->