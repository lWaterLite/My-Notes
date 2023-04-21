### 创建数据库

```sqlite
.open dbname.db
```

### 查看数据库列表

```sqlite
.databases
```

### 导出/导出

```sqlite
dbname.db .dump > filename.sql
dbname < filename.sql
```

### 附加数据库

```sqlite
ATTACH DATABASE 'dbname.db' as 'alias';
```

