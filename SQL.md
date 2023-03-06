## SQL语句

### DDL-Data Definition Language

#### 数据库操作

- 查询

  ```sql
  SHOW DATABASES;	-- 查询所有数据库
  ```

  ```SQL
  SELECT DATABASES(); -- 查询当前数据库
  ```

- 创建

  ```sql
  CREATE DATABASE [IF NOT EXISTS] <dbname> [DEFAULT CHARSET charsetname] [COLLATE rules]; -- 创建一个数据库
  ```

- 删除

  ```sql
  DROP DATABASE [IF EXISTS] <dbname>; -- 删除数据库
  ```

- 使用

  ```sql
  USE <dbname>; -- 使用数据库
  ```

#### 表操作-查询

- 查询当前数据库所有表

  ```sql
  SHOW TABLES;
  ```

- 查询表结构

  ```SQL
  DESC <tablename>;
  ```

- 查询指定表的建表语句

  ```sql
  SHOW CREATE TABLE <tablename>;
  ```

#### 表操作-创建

- 创建表

  ```sql
  CREATE TABLE <tablename> (field1 field1type [COMMENT field1comment], field2 field2type [COMMENT field2comment]...) [COMMENT tablecomment];
  ```

#### 表操作-修改

-  添加字段

  ```sql
  ALTER TABLE <tablename> ADD <fieldname> <fieldtype> [COMMENT fieldcomment] [constraints];
  ```

- 修改数据类型

  ```sql
  ALTER TABLE <tablename> MODIFY <fieldname> <fieldtype>;
  ```

- 修改字段名和字段类型

  ```sql
  ALTER TABLE <tablename> CHANGE <oldFieldname> <newFieldName> <fieldtype> [COMMENT fieldcomment] [constraints];
  ```

- 删除字段

  ```SQL
  ALTER TABLE <tablename> DROP <fieldname>;
  ```

- 修改表名

  ```SQL
  ALTER TABLE <tablename> RENAME TO <newTablename>;
  ```

- 删除表

  ```SQL
  DROP TABLE [IF EXISTS] <tablename>;
  ```

- 删除指定表，并重新创建该表

  ```SQL
  TRUNCATE TABLE <tablename>;
  ```


### DML-Data Manipulation Language

#### 添加数据

- 给指定字段添加数据

  ```sql
  INSERT INTO <tablename> (field1, field2, ...) VALUES (value1, value2, ...)  [,(value1, value2, ...), ...]; -- 单个添加或批量添加
  ```

- 给全部字段添加数据

  ```sql
  INSERT INTO <tablename> VALUES (value1, value2, ...)  [,(value1, value2, ...), ...]; -- 单个添加或批量添加
  ```

#### 修改数据

```sql
 UPDATE <tablename> SET <field1=value1>, [field2=value2, ...] [WHERE conditions];
```

#### 删除数据

```sql
DELETE FROM <tablename> [WHERE conditions];
```

### DQL-Data Query Language

#### 通用语法

```sql
SELECT <fieldList> FROM <tableList> [WHERE <conditionList> GROUP BY <groupfieldList> HAVING <groupedConditionList> ORDER BY <orderfieldList> LIMIT <pageParma>];
```

#### 基本查询

- 查询多个字段

  ```sql
  SELECT [DISTINCT] <field1> [AS alias1][, field2 [AS alias2], ...] FROM <tablename>;
  -- [AS alias]用于设置别名
  -- [DISTINCT]用于去除查询结果中重复的记录
  ```

- 查询全部字段

  ```SQL
  SELECT * FROM <tablename>;
  ```

#### 条件查询

- 语法

  ```sql
  SELECT <fieldList> FROM <tablename> WHERE <conditionList>；
  ```


- 条件

	| 运算符              | 功能                                     |
  | ------------------- | ---------------------------------------- |
  | >                   | 大于                                     |
  | >=                  | 大于等于                                 |
  | <                   | 小于                                     |
  | <=                  | 小于等于                                 |
  | =                   | 等于                                     |
  | <> 或 !=            | 不等于                                   |
  | BETWEEN ... AND ... | 在某个范围之内(含最大最小值)             |
  | IN(...)             | 在in之后的列表中的值，多选一             |
  | LIKE 占位符         | 模糊匹配(_匹配单个字符，%匹配任意个字符) |
  | IS NULL             | 为NULL                                   |
  | AND 或 &&           | 与                                       |
  | OR 或 \|\|          | 或                                       |
  | NOT 或 !            | 非                                       |

#### 聚合函数

- 介绍

  将一列数据作为一个整体，进行纵向计算

- 常见聚合函数

  | 函数  | 功能     |
  | ----- | -------- |
  | count | 统计数据 |
  | max   | 最大值   |
  | min   | 最小值   |
  | avg   | 平均值   |
  | sum   | 求和     |

- 注意

  聚合函数运算时，null值不参与

#### 分组查询

- 语法

  ```sql
  SELECT <fieldList> FROM <tablename> [WHERE conditons] GROUP BY <groupedFieldname> [HAVING groupedConditions];
  ```

- 注意

  - WHERE在分组之前进行过滤，HAVING在分组后进行过滤
  - WHERE不可对聚合函数进行判断，HAVING可以

####  排序查询

- 语法

  ```SQL
  SELECT <fieldList> FROM <tablename> ORDER BY <field1> <order1>, [<field2> <order2>, ...];
  -- 排序支持多字段排序
  -- order为排序方式
  ```

- 排序方式

  - ASC: 升序(默认值)
  - DESC: 降序

#### 分页查询

- 语法

  ```SQL
  SELECT <fieldList> FROM <tablename> LIMIT <beginIndex>, <queryCount>;
  ```

### DCL-Data Control Language

#### 管理用户

- 查询用户

  ```SQL
  USE mysql;
  SELECT * FROM user;
  -- mysql数据库所有的用户信息都存放在mysql数据库的user表中
  ```

- 创建用户

  ```SQL
  CREATE USER <username>@<hostname> IDENTIFIED BY <password>;
  ```

- 修改用户密码

  ```sql
  ALTER USER <username>@<hostname> IDENTIFIED WITH <oldPassword> <newPassword>;
  ```

- 删除用户

  ```SQL
  DROP USER <username>@<hostname>;
  ```


#### 权限控制

- 常用权限

  | 权限                | 说明             |
  | ------------------- | ---------------- |
  | ALL, ALL PRIVILEGES | 所有权限         |
  | SELECT              | 查询数据         |
  | INSERT              | 插入数据         |
  | UPADATE             | 修改数据         |
  | ALTER               | 修改表           |
  | DROP                | 删除库、表、视图 |
  | CREATE              | 创建数据库/表    |

- 查询权限

  ```sql
  SHOW GRANTS FOR <username>@<hostname>;
  ```

- 授予权限

  ```sql
  GRANT <permissons> ON <databasename>.<tablename> TO <username>@<hostname>;
  ```

- 撤销权限

  ```sql
  REVOKE <permissions> ON <databasename>.<tablename> TO <username>@<hostname>;
  ```

---------

## 函数

### 常用字符串函数

| 函数                       | 功能                                                |
| -------------------------- | --------------------------------------------------- |
| CONCAT(S1, S2, ...)        | 字符串拼接，将S1, S2, ...拼接成一个字符串           |
| LOWER(str)                 | 将字符串str全部转成小写                             |
| UPPER(str)                 | 将字符串str全部转成大写                             |
| LPAD(str, n, pad)          | 左填充，用字符串pad对str的左边进行填充，使其长度为n |
| RPAD(str, n, pad)          | 右填充，用字符串pad对str的右边进行填充，使其长度为n |
| TRIM(str)                  | 去掉字符串头部和为尾部的空格                        |
| SUBSTRING(str, start, len) | 返回字符串str从start位置开始的len个长度的子串       |

### 常用数值函数

| 函数        | 功能                             |
| ----------- | -------------------------------- |
| CEIL(x)     | 向上取整                         |
| FLOOR(x)    | 向下取整                         |
| MOD(x, y)   | 返回x/y的模                      |
| RAND()      | 返回0~1内的随机数                |
| ROUND(x, y) | 求参数x的四舍五入值，保留y位小数 |

### 常见日期函数

| 函数                               | 功能                                            |
| ---------------------------------- | ----------------------------------------------- |
| CURDATE()                          | 返回当前日期                                    |
| CURTIME()                          | 返回当前时间                                    |
| NOW()                              | 返回当前日期和时间                              |
| YEAR(date)                         | 获取指定date的年份                              |
| MONTH(date)                        | 获取指定date的月份                              |
| DAY(date)                          | 获取指定date的日期                              |
| DATE_ADD(date, INTERVAL expr type) | 返回一个日期/时间加上一个时间间隔expr后的时间值 |
| DATEIFF(date1， date2)             | 返回其实时间date1和结束时间date2之间的天数      |

### 常用流程控制函数

| 函数                                                       | 功能                                                |
| ---------------------------------------------------------- | --------------------------------------------------- |
| IF(value, t, f)                                            | 如果value为true，则返回t，否则返回f                 |
| IFNULL(value1， value2)                                    | 如果value1非空，返回value1，否则返回value2          |
| CASE WHEN [value1] THEN [res1] ... ELSE [default] END      | 如果val1返回res1， ...否则返回default               |
| CASE [expr] WHEN [val1] THEN [res1] ... ELSE [default] END | 如果expr的值等于val1，返回res1， ...否则返回default |

## 约束

### 概述

1. 概念：约束是作用于表中字段上的规则，用于限制存储在表中的数据。 

2. 目的：保证数据库中的数据的正确，有效和完整。

3. 分类：

   | 约束     | 描述                                                     | 关键字         |
   | -------- | -------------------------------------------------------- | -------------- |
   | 非空约束 | 限制该字段的数据不能为null                               | NOT NULL       |
   | 唯一约束 | 保证该字段的所有数据都是唯一、不重复的                   | UNIQUE         |
   | 主键约束 | 主键是一行数据的唯一标识，要求非空且唯一                 | PRIMARY KEY    |
   | 默认约束 | 保存数据时，如果未指定该字段的值，则采用默认值           | DEFAULT        |
   | 检查约束 | 保证字段值满足某一个条件                                 | CHECK          |
   | 外键约束 | 用来让两张表的数据之间建立连接，保证数据的一致性和完整性 | FOREIGN KEY    |
   | 自动增长 |                                                          | AUTO_INCREMENT |


###    外键

- 添加外键

  ```SQL
  CREATE TABLE <tablename> (
  	fieldname type,
      ...,
      [CONSTRAINT] [foreignKeyName] FOREIGN KEY (foreignKeyFieldname) REFERENCES <tablename>(fieldname)
  );
  ```

  ```SQL
  ALTER TABLE <tablename> ADD CONSTRAINT <foreignKeyName> FOREIGN KEY (foreignKeyFieldname) REFERENCES <tablename>(fieldname);
  ```

- 删除外键

  ```sql
  ALTER TABLE <tablename> DROP FOREIGN KEY <foreignKeyName>;
  ```

- 删除/更新行为

  | 行为        | 说明                                                         |
  | ----------- | ------------------------------------------------------------ |
  | NO ACTION   | 在父表中删除/更新对应的记录时，首先检查该记录是否有对应外键，有则不允许删除/更新。(与RESTRICT一致) |
  | RESTRICT    | 同 NO ACTION                                                 |
  | CASCADE     | 在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有，则也删除/更新外键在子表中的记录。 |
  | SET NULL    | 在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有，则设置子表中该外键值为NULL |
  | SET DEFAULT | 父表变更时。子表将外键设置成一个默认值(Innodb不支持  )       |

  ```sql
  ALTER TABLE <tablename> DROP FOREIGN KEY <foreignKeyName> ON UPDATE CASCADE ON DELETE CASCADE;
  ```

  

