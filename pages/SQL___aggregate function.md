alias:: 聚合函数

- 在 SQL 中，聚合函数（Aggregate Functions）用于执行计算在一组值上，并返回单个值。这些函数通常在执行描述统计分析时使用，如计算总和、平均值、最大值或最小值等。聚合函数在 `SELECT` 语句的 `GROUP BY` 子句中尤其有用，因为它们可以对数据分组进行汇总计算。
  
  下面列出了一些常见的 SQL 聚合函数及其用途：
	- ### COUNT 
	  logseq.order-list-type:: number
	  返回指定列的值的数量。
	  ```sql
	  SELECT COUNT(EmployeeID) FROM Employees;
	  ```
	  这个例子会返回 `Employees` 表中的员工总数。
	- ### SUM 
	  logseq.order-list-type:: number
	  计算指定列的数值总和。
	  ```sql
	  SELECT SUM(Salary) FROM Employees;
	  ```
	  这个例子会计算 `Employees` 表中所有员工的薪水总和。
	- ### AVG 
	  logseq.order-list-type:: number
	  计算指定列的平均值。
	  ```sql
	  SELECT AVG(Salary) FROM Employees;
	  ```
	  这个例子会计算 `Employees` 表中所有员工的平均薪水。
	- ### MAX 
	  logseq.order-list-type:: number
	  返回一列中的最大值。
	  ```sql
	  SELECT MAX(Salary) FROM Employees;
	  ```
	  这个例子会找出 `Employees` 表中最高的薪水。
	- ### MIN 
	  logseq.order-list-type:: number
	  返回一列中的最小值。
	  ```sql
	  SELECT MIN(Salary) FROM Employees;
	  ```
	  这个例子会找出 `Employees` 表中最低的薪水。
	- ### GROUP_CONCAT 
	  logseq.order-list-type:: number
	  将列值组合成一个单独的字符串，通常用于 `GROUP BY` 子句。
	  ```sql
	  SELECT Department, GROUP_CONCAT(EmployeeName) FROM Employees GROUP BY Department;
	  ```
	  这个例子会显示每个部门的所有员工名字，名字将在一个单独的字符串中显示。
	- ### STDDEV 
	  logseq.order-list-type:: number
	  计算一组值的标准差，表示数据的离散程度。
	  ```sql
	  SELECT STDDEV(Salary) FROM Employees;
	  ```
	  这个例子会计算 `Employees` 表中员工薪水的标准差。
	- ### VAR_POP 和 VAR_SAMP 
	  logseq.order-list-type:: number
	  分别计算一组值的总体方差和样本方差。
	  ```sql
	  SELECT VAR_POP(Salary) FROM Employees;
	  SELECT VAR_SAMP(Salary) FROM Employees;
	  ```
	  这些例子计算薪水的总体方差和样本方差。
- 聚合函数是数据分析和报告的强大工具，使得从大量数据中快速提取有用的统计信息成为可能。在实际应用中，这些函数常常与 `GROUP BY` 子句结合使用，以对数据进行分类和汇总分析。<!--Converted by ToLogseq-->
  logseq.order-list-type:: number