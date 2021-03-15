# SQL 實作

## 新增資料庫

```sql
create database labs
```

## 秀出資料

工作產生指令馬

```sql
CREATE TABLE [GUIDdemo]
(
[GUID] uniqueidentifier not null default newsequentialid(),
COL1 VARCHAR(10)
)
INSERT [GUIDdemo] (COL1) SELECT '第一列'
SELECT * FROM [GUIDdemo];
```

![](.gitbook/assets/image%20%2811%29.png)



