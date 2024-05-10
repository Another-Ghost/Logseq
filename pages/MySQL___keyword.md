- MySQL 支持许多关键字和保留字，这些词用于执行特定的数据库操作、定义数据结构或控制事务等。这里列举一些常见的 MySQL 关键字，并提供每个关键字的使用示例：
- ### SELECT
  logseq.order-list-type:: number
  用于从数据库表中检索数据。
  ```sql
  SELECT name, age FROM users WHERE age > 18;
  ```
- ### INSERT
  logseq.order-list-type:: number
  用于向表中添加新的行。
  ```sql
  INSERT INTO users (name, age) VALUES ('Alice', 22);
  ```
- ### UPDATE
  logseq.order-list-type:: number
  用于修改表中的数据。
  ```sql
  UPDATE users SET age = 23 WHERE name = 'Alice';
  ```
- ### DELETE
  logseq.order-list-type:: number
  用于从表中删除数据。
  ```sql
  DELETE FROM users WHERE name = 'Alice';
  ```
- ### CREATE
  logseq.order-list-type:: number
  用于创建新的数据库对象，如数据库、表、视图等。
  ```sql
  CREATE TABLE users (id INT PRIMARY KEY, name VARCHAR(100), age INT);
  ```
- ### DROP
  logseq.order-list-type:: number
  用于删除数据库对象。
  ```sql
  DROP TABLE users;
  ```
- ### ALTER
  logseq.order-list-type:: number
  用于修改数据库表的结构。
  ```sql
  ALTER TABLE users ADD email VARCHAR(255);
  ```
- ### JOIN
  logseq.order-list-type:: number
  用于结合两个或多个表的行。
  ```sql
  SELECT users.name, orders.amount FROM users JOIN orders ON users.id = orders.user_id;
  ```
- ### WHERE
  logseq.order-list-type:: number
  用于指定选择条件。
  ```sql
  SELECT * FROM users WHERE age >= 18;
  ```
- ### 10. GROUP BY
  用于根据一个或多个列对结果集进行分组。
  ```sql
  SELECT age, COUNT(*) FROM users GROUP BY age;
  ```
- ### 11. ORDER BY
  用于对结果集进行排序。
  ```sql
  SELECT name, age FROM users ORDER BY age DESC;
  ```
- ### 12. LIMIT
  用于限制查询结果的数量。
  ```sql
  SELECT * FROM users LIMIT 10;
  ```
- ### 13. UNION
  用于合并两个或多个 SELECT 语句的结果集。
  ```sql
  SELECT name FROM users UNION SELECT name FROM admins;
  ```
- ### 14. LIKE
  用于在 WHERE 子句中搜索列中的指定模式。
  ```sql
  SELECT * FROM users WHERE name LIKE 'A%';
  ```
- ### 15. BETWEEN
  用于在 WHERE 子句中选择给定范围内的值。
  ```sql
  SELECT * FROM users WHERE age BETWEEN 18 AND 25;
  ```
- ### 16. IN
  用于在 WHERE 子句中指定多个可能的值。
  ```sql
  SELECT * FROM users WHERE name IN ('Alice', 'Bob');
  ```
- ### 17. CASE
  用于在 SQL 语句中执行 IF-THEN-ELSE 类型的操作。
  ```sql
  SELECT name, age, CASE WHEN age >= 18 THEN 'adult' ELSE 'minor' END AS status FROM users;
  ```
- ### 18. DISTINCT
  用于返回唯一不同的值。
  ```sql
  SELECT DISTINCT status FROM users;
  ```
- ### 19. HAVING
  用于在 `GROUP BY` 后对结果集进行条件过滤。
  ```sql
  SELECT age, COUNT(*) AS count FROM users GROUP BY age HAVING count > 1;
  ```
- ### 20. EXISTS
  用于测试子查询是否返回数据。
  ```sql
  SELECT * FROM users WHERE EXISTS (SELECT * FROM orders WHERE users.id = orders.user_id);
  ```
- ### 21. REPLACE
  用于插入新行或在行存在时替换它。
  ```sql
  REPLACE INTO users (id, name, age) VALUES (1, 'Alice', 24);
  ```
- ### 22. TRUNCATE
  用于删除表中的数据，但不删除表本身。
  ```sql
  TRUNCATE TABLE users;
  ```
- ### 23. INDEX
  用于在表中创建索引，以提高查询效率。
  ```sql
  CREATE INDEX idx_name ON users(name);
  ```
- ### 24. VIEW
  用于创建一个视图，视图是可查询的表格结果集。
  ```sql
  CREATE VIEW active_users AS SELECT * FROM users WHERE status = 'active';
  ```
- ### 25. LOCK
  用于控制对表的访问。
  ```sql
  LOCK TABLES users WRITE;
  ```
- ### 26. UNLOCK
  用于释放对表的锁定。
  ```sql
  UNLOCK TABLES;
  ```
- ### 27. COMMIT
  用于提交事务，使所有数据变更成为永久性。
  ```sql
  BEGIN;
  UPDATE accounts SET balance = balance - 100 WHERE id = 1;
  UPDATE accounts SET balance = balance + 100 WHERE id = 2;
  COMMIT;
  ```
- ### 28. ROLLBACK
  用于回滚事务中的命令，撤销所有未提交的修改。
  ```sql
  BEGIN;
  INSERT INTO users (name, age) VALUES ('John', 25);
  ROLLBACK;
  ```
- ### 29. SAVEPOINT
  用于在事务中设置一个保存点，可以回滚到该点。
  ```sql
  BEGIN;
  INSERT INTO users (name, age) VALUES ('John', 25);
  SAVEPOINT sp1;
  UPDATE users SET age = 26 WHERE name = 'John';
  ROLLBACK TO sp1;
  COMMIT;
  ```
- ### 30. DECLARE
  用于在存储过程中声明局部变量。
  ```sql
  DECLARE myVariable INT DEFAULT 10;
  ```
-
-