- 在 SQL 中，`ON DELETE` 子句是在创建或修改外键约束时使用的，用来定义当主键表（父表）中的记录被删除时，如何处理外键表（子表）中与之相关联的记录。这种关系管理是数据库完整性的关键部分，确保了数据之间的逻辑一致性和引用完整性。
- ### `ON DELETE` 触发的操作类型
	- **NO ACTION (或 RESTRICT)**
	  logseq.order-list-type:: number
		- 这是默认行为，如果尝试删除父表中有子表依赖的记录，则操作会失败，并抛出错误。`NO ACTION` 和 `RESTRICT` 在大多数数据库中功能相同，阻止删除操作。
		- 示例：
		  ```sql
		  ALTER TABLE Orders
		  ADD CONSTRAINT fk_customer
		  FOREIGN KEY (CustomerID)
		  REFERENCES Customers(CustomerID)
		  ON DELETE NO ACTION;
		  ```
	- **CASCADE**
	  logseq.order-list-type:: number
		- 如果父表中的记录被删除，那么子表中所有依赖这条记录的行也将被自动删除。这对于删除操作需要连锁反应的情况非常有用。
		- 示例：
		  ```sql
		  ALTER TABLE Orders
		  ADD CONSTRAINT fk_customer
		  FOREIGN KEY (CustomerID)
		  REFERENCES Customers(CustomerID)
		  ON DELETE CASCADE;
		  ```
	- **SET NULL**
	  logseq.order-list-type:: number
		- 当父表中的相关记录被删除时，子表中的外键列将被设置为 `NULL`。这需要外键列允许 `NULL` 值。
		- 示例：
		  ```sql
		  ALTER TABLE Orders
		  ADD CONSTRAINT fk_customer
		  FOREIGN KEY (CustomerID)
		  REFERENCES Customers(CustomerID)
		  ON DELETE SET NULL;
		  ```
	- **SET DEFAULT**
	  logseq.order-list-type:: number
		- 类似于 `SET NULL`，但是当父表中的记录被删除时，子表中的外键列将被设置为一个默认值。这要求已经为外键列定义了默认值。
		- 示例：
		  ```sql
		  ALTER TABLE Orders
		  ADD CONSTRAINT fk_customer
		  FOREIGN KEY (CustomerID)
		  REFERENCES Customers(CustomerID)
		  ON DELETE SET DEFAULT;
		  ```
- ### 使用场景和考虑因素
	- 使用 `ON DELETE` 子句可以确保数据的引用完整性，避免出现孤立的记录，即存在外键引用但缺少相应主键的记录。
	- 在选择适当的 `ON DELETE` 行为时，需要考虑应用的业务逻辑。例如，使用 `CASCADE` 可以方便地清理数据，但在某些情况下可能会意外地删除大量数据。
	- 考虑到 `SET NULL` 和 `SET DEFAULT` 的使用，要确保这些操作不会违反业务规则或导致数据状态不一致。