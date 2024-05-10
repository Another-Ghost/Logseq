alias:: 子查询

- 在 SQL 中，子查询（subquery）是嵌套在其他 SQL 查询中的查询。子查询可以出现在 `SELECT`、`INSERT`、`UPDATE`、`DELETE` 语句中，以及在 `FROM`、`WHERE` 和 `HAVING` 子句中。子查询使得 SQL 语句能够更加强大和灵活，因为它们允许在一个查询中嵌入另一个查询，从而实现更复杂的数据操作和条件逻辑。
- ### 子查询的类型
	- **标量子查询**：
	  logseq.order-list-type:: number
		- 返回单个值的子查询，常见于 `SELECT` 列表中或 `WHERE` 子句中作为条件。
		- 示例：
		  ```sql
		  SELECT Name, (SELECT COUNT(*) FROM Orders WHERE CustomerID = C.CustomerID) AS OrderCount
		  FROM Customers C;
		  ```
		  这个查询显示每个客户及其订单数量。
	- **相关子查询**：
	  logseq.order-list-type:: number
		- 子查询中的选择条件依赖于外部查询的某个值，每处理外部查询的一行数据就需要执行一次子查询。
		- 示例：
		  ```sql
		  SELECT e.Name, e.Salary
		  FROM Employees e
		  WHERE e.Salary > (
		  SELECT AVG(Salary)
		  FROM Employees
		  WHERE DepartmentID = e.DepartmentID
		  );
		  ```
		  这个查询返回薪资高于本部门平均薪资的员工。
	- **从句子查询**：
	  logseq.order-list-type:: number
		- 出现在 `FROM` 子句中，作为一个临时表，供主查询使用。
		- 示例：
		  ```sql
		  SELECT avg_data.AvgSalary
		  FROM (
		  SELECT DepartmentID, AVG(Salary) AS AvgSalary
		  FROM Employees
		  GROUP BY DepartmentID
		  ) avg_data;
		  ```
		  这个查询首先计算每个部门的平均薪资，然后从中选择结果。
	- **存在子查询**（EXISTS）：
	  logseq.order-list-type:: number
		- 存在子查询通常用在 `WHERE` 子句中，检查一组记录的存在性。
		- 示例：
		  ```sql
		  SELECT ProductName
		  FROM Products p
		  WHERE EXISTS (
		  SELECT *
		  FROM OrderDetails
		  WHERE ProductID = p.ProductID AND Quantity >= 100
		  );
		  ```
		  这个查询返回至少在一笔订单中被订购100件以上的产品。
- ### 子查询的优点和注意事项
	- **优点**：子查询可以使得查询逻辑更加直观和模块化，特别是当处理复杂的数据检索需求时。
	- **注意事项**：
		- 性能：尤其是相关子查询可能会影响查询性能，因为对于主查询的每一行都要执行一次子查询。
		- 可读性：嵌套过多的子查询可能会使 SQL 语句难以阅读和维护。
		  
		  正确使用子查询可以大幅提升 SQL 的能力，使得数据分析和处理更加灵活和强大。然而，为了维护查询的性能和可管理性，应该适度使用子查询，并在必要时考虑使用连接（JOIN）或其他方法替代。<!--Converted by ToLogseq-->