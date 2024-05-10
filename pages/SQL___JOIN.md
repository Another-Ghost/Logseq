- 在 SQL 中，`JOIN` 语句用于结合两个或多个数据库表的行。通过 `JOIN`，可以从两个表中提取并结合相关的数据行，创建一个包含这些表中所有相关数据的新结果集。这是数据库查询中非常重要的功能，尤其是在处理关系型数据库时，因为它允许用户有效地查询跨多个表的复杂数据。
- ### 常见的 SQL JOIN 类型
	- **INNER JOIN**
	  logseq.order-list-type:: number
		- 返回两个表中匹配的记录。如果在一个表中的行与另一个表中的行在特定列上的值相等，则 `INNER JOIN` 会返回这些行。
		- **示例**：
		  ```sql
		  SELECT Employees.Name, Orders.OrderID
		  FROM Employees
		  INNER JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
		  ```
	- **LEFT JOIN**（或 **LEFT OUTER JOIN**）
	  logseq.order-list-type:: number
		- 返回左表（`FROM` 之后的表）中的所有记录以及两个表中匹配的记录。如果右表没有匹配，则结果中右表的部分会包含 NULL。
		- **示例**：
		  ```sql
		  SELECT Employees.Name, Orders.OrderID
		  FROM Employees
		  LEFT JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
		  ```
	- **RIGHT JOIN**（或 **RIGHT OUTER JOIN**）
	  logseq.order-list-type:: number
		- 与 `LEFT JOIN` 相反，返回右表中的所有记录以及两个表中匹配的记录。如果左表没有匹配，则结果中左表的部分会包含 NULL。
		- **示例**：
		  ```sql
		  SELECT Employees.Name, Orders.OrderID
		  FROM Employees
		  RIGHT JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
		  ```
	- **FULL JOIN**（或 **FULL OUTER JOIN**）
	  logseq.order-list-type:: number
		- 返回两个表中的所有记录。当某一侧的行没有匹配时，另一侧的对应列会包含 NULL。
		- **示例**：
		  ```sql
		  SELECT Employees.Name, Orders.OrderID
		  FROM Employees
		  FULL JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
		  ```
	- **CROSS JOIN**
	  logseq.order-list-type:: number
		- 返回第一个表中的每一行与第二个表中每一行的笛卡尔积。不需要任何匹配条件。
		- **示例**：
		  ```sql
		  SELECT Employees.Name, Orders.OrderID
		  FROM Employees
		  CROSS JOIN Orders;
		  ```
	- **SELF JOIN**
	  logseq.order-list-type:: number
		- 表与自身进行连接。通常用于比较表内的不同行。
		- **示例**：
		  ```sql
		  SELECT A.Name AS EmployeeName1, B.Name AS EmployeeName2
		  FROM Employees A, Employees B
		  WHERE A.EmployeeID <> B.EmployeeID AND A.DepartmentID = B.DepartmentID;
		  ```
- ### 使用 JOIN 的注意事项
	- 确保在使用 `JOIN` 时明确指定连接条件，否则可能不小心创建一个耗费资源的笛卡尔积。
	- 在使用 `OUTER JOIN` 时考虑可能出现的 NULL 值，确保查询逻辑能正确处理这些情况。
	- 使用合适的索引优化 `JOIN` 操作，以提升查询性能，特别是在处理大数据集时。
	  
	  `JOIN` 语句是 SQL 中非常强大的工具，能够帮助你解决多种数据组合的需求，提供灵活而有效的数据分析和报告方式。<!--Converted by ToLogseq-->