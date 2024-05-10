- 在 SQL 中，`UNION` 操作符用于合并两个或多个 [[`SELECT`]] 语句的[[结果集]]，返回一个包含所有记录的结果集。使用 `UNION` 的关键在于每个 `SELECT` 语句必须具有相同数量的列，列的数据类型也需要相匹配，并且每个查询中的列必须按相同的顺序排列。
- ### UNION 的主要特点
  collapsed:: true
	- **删除重复行**：`UNION` 默认会去除结果中的重复行，只显示唯一的记录。
	  logseq.order-list-type:: number
	- **性能考虑**：因为 `UNION` 操作需要检查重复的记录并删除它们，所以可能对性能有一定影响。
	  logseq.order-list-type:: number
- ### 使用 UNION 的例子
  假设我们有两个表，`Products_A` 和 `Products_B`，它们存储了不同类别的产品信息。使用 `UNION` 来合并两个表中的产品名列表：
  ```sql
  SELECT ProductName FROM Products_A
  UNION
  SELECT ProductName FROM Products_B;
  ```
  
  这个查询会返回两个表中所有不重复的产品名称。
- ### UNION ALL
  
  如果不需要自动去重，可以使用 `UNION ALL` 命令。`UNION ALL` 将包括所有结果，不会排除重复的行。
- ### 使用 UNION ALL 的例子
  
  ```sql
  SELECT ProductName FROM Products_A
  UNION ALL
  SELECT ProductName FROM Products_B;
  ```
  
  这个查询将返回两个表中所有的产品名称，包括重复的。
- ### 使用场景
  
  `UNION` 和 `UNION ALL` 都可以用于多种数据整合的场景，比如：
	- 合并多个表中的相似数据到一个统一的视图。
	- 从不同的数据源中聚合数据，用于报表或分析。
	- 组合多个查询的结果作为复杂查询的一部分。
- ### 注意事项
	- 在使用 `UNION` 时确保每个查询中的列具有相同的数据类型，这是因为数据类型不匹配会导致错误。
	- 考虑到 `UNION` 会去重，如果查询大量数据时，可能会有较大的性能开销。如果不需要去重，建议使用 `UNION ALL` 以提高性能。
	  
	  通过有效地使用 `UNION` 和 `UNION ALL`，可以在数据库查询中实现灵活的数据整合和处理，这对于数据分析和报告尤其有用。<!--Converted by ToLogseq-->