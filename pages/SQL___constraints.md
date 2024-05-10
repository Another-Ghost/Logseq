- 在SQL中，约束（Constraints）用于指定数据表中数据的规则，保证数据库的准确性和可靠性。约束能够强制执行数据库的完整性和业务规则。以下是一些最常见的SQL约束类型：
	- ### PRIMARY KEY 
	  logseq.order-list-type:: number
	  一个或多个字段的组合，能够唯一地标识表中的每行记录。它必须包含唯一的值，且不能包含NULL值。
	  ```sql
	  CREATE TABLE Customers (
	    CustomerID int NOT NULL,
	    CustomerName varchar(255) NOT NULL,
	    PRIMARY KEY (CustomerID)
	  );
	  ```
	- ### FOREIGN KEY 
	  logseq.order-list-type:: number
	  一个字段（或字段组合），用于在两个表之间建立和维护联系。它指向另一个表中的PRIMARY KEY。
	  ```sql
	  CREATE TABLE Orders (
	    OrderID int NOT NULL,
	    OrderNumber int NOT NULL,
	    CustomerID int,
	    PRIMARY KEY (OrderID),
	    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
	  );
	  ```
	- ### NOT NULL 
	  logseq.order-list-type:: number
	  确保列不接受NULL值。这强制在插入或更新记录时必须为该列提供值。
	  ```sql
	  CREATE TABLE Employees (
	    EmployeeID int NOT NULL,
	    LastName varchar(255) NOT NULL,
	    FirstName varchar(255) NOT NULL
	  );
	  ```
	- ### UNIQUE 
	  logseq.order-list-type:: number
	  保证所有列中的每行必须有唯一的值。一个表可以有多个UNIQUE约束。
	  ```sql
	  CREATE TABLE Products (
	    ProductID int NOT NULL,
	    ProductCode varchar(50) NOT NULL,
	    UNIQUE (ProductCode)
	  );
	  ```
	- ### CHECK 
	  logseq.order-list-type:: number
	  确保列中的所有值满足一个指定的条件。它可以定义在单个列或整个表的水平上。
	  ```sql
	  CREATE TABLE Products (
	    ProductID int NOT NULL,
	    Price decimal NOT NULL,
	    CHECK (Price > 0)
	  );
	  ```
	- ### DEFAULT 
	  logseq.order-list-type:: number
	  为列定义默认值。如果在插入行时没有提供该列的值，将会添加默认值。
	  ```sql
	  CREATE TABLE Employees (
	    EmployeeID int NOT NULL,
	    HireDate date NOT NULL,
	    Status varchar(10) DEFAULT 'active'
	  );
	  ```
	- ### INDEX 
	  logseq.order-list-type:: number
	  虽然不是一个约束，但经常与约束一起讨论。索引用于提高数据库表的数据检索速度。它不是强制性的，但是可以显著加快查询速度。
	  ```sql
	  CREATE INDEX idx_lastname ON Employees (LastName);
	  ```
	- ### CASCADE 
	  logseq.order-list-type:: number
	  `CASCADE`是在设置外键约束时可以选择的一个选项，用于自动更新或删除相关联的行。例如，如果父表中的行被删除或更新，那么子表中的匹配行也将自动更新或删除。
		- **ON DELETE CASCADE**：当参照的主键被删除时，也删除包含该外键的行。
		  logseq.order-list-type:: number
		  ```sql
		  CREATE TABLE Orders (
		  OrderID int NOT NULL,
		  ProductID int,
		  Quantity int,
		  PRIMARY KEY (OrderID),
		  FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
		  ON DELETE CASCADE
		  );
		  ```
		- **ON UPDATE CASCADE**：当参照的主键被更新时，也更新包含该外键的行。
		  logseq.order-list-type:: number
		  ```sql
		  CREATE TABLE Orders (
		  OrderID int NOT NULL,
		  CustomerID int,
		  OrderDate date,
		  PRIMARY KEY (OrderID),
		  FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
		  ON UPDATE CASCADE
		  );
		  ```
	- ### SET NULL 
	  logseq.order-list-type:: number
	  这是另一个外键约束选项，用于在删除或更新关联行时将外键列设置为NULL。
		- **ON DELETE SET NULL**：当外键的参照主键被删除时，将外键的值设置为NULL。
		  logseq.order-list-type:: number
		  ```sql
		  CREATE TABLE Orders (
		  OrderID int NOT NULL,
		  CustomerID int,
		  PRIMARY KEY (OrderID),
		  FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
		  ON DELETE SET NULL
		  );
		  ```
	- ### NO ACTION
	  logseq.order-list-type:: number
	  `NO ACTION`关键字指定，如果尝试删除或更新一个主键，而这个主键被其他外键约束引用，则抛出错误。
		- **ON DELETE NO ACTION**：如果有外键依赖，尝试删除主键将失败。
		  logseq.order-list-type:: number
		  ```sql
		  CREATE TABLE Orders (
		  OrderID int NOT NULL,
		  CustomerID int,
		  PRIMARY KEY (OrderID),
		  FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
		  ON DELETE NO ACTION
		  );
		  ```
	- ### SET DEFAULT
	  logseq.order-list-type:: number
	  这是一个相对少见的外键选项，用于将外键字段设置为默认值（如果存在）当主键行被删除或修改时。
		- **ON DELETE SET DEFAULT**：当外键的参照主键被删除时，将外键的值设置为默认值。
		  logseq.order-list-type:: number
		  ```sql
		  CREATE TABLE Orders (
		  OrderID int NOT NULL,
		  CustomerID int DEFAULT 1,
		  PRIMARY KEY (OrderID),
		  FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
		  ON DELETE SET DEFAULT
		  );
		  ```
	- ### 实践中的注意事项
	  logseq.order-list-type:: number
	  使用这些约束时，需要仔细考虑它们对数据完整性的影响以及它们如何支持或实现业务规则。例如，`CASCADE`选项可能会导致意外删除大量数据，而`SET NULL`可能导致数据分析时出现问题，因为相关字段的数据可能丢失。设计数据库时，这些约束应该与应用程序的业务逻辑和数据处理需求相一致。
	  
	  这些约束增强了数据库的健壮性，并帮助维护数据一致性和完整性，是任何数据库设计和应用开发中不可或缺的工具。<!--Converted by ToLogseq-->