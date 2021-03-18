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

![](../.gitbook/assets/image%20%2812%29.png)

```sql
USE [LABS]
GO

INSERT INTO [dbo].[STOCK_PRICE]
           ([SYMBOL]
           ,[DATE]
           ,[QTY]
           ,[OPEN]
           ,[HIGH]
           ,[LOW]
           ,[CLOSE])
 select '2330' [SYMBOL]
			,[DATE]
           ,Volume[QTY]
           ,[OPEN]
           ,[HIGH]
           ,[LOW]
           ,[CLOSE]
from [dbo].[2330.TW (1)]
```

![](../.gitbook/assets/image%20%2811%29.png)

```sql
select * from [dbo].[STOCK_PRICE]
where DATE> '2021-1-1' and SYMBOL='0050'
```

```sql
DECLARE @MAXNO	VARCHAR(5)
/*1.從資料表取最大流水號*/
SELECT @MAXNO=ISNULL(MAX(SERIAL),'00000') FROM STOCK_NAME_SERIAL
PRINT @MAXNO

/*2.最大流水號+1*/
SELECT @MAXNO=CONVERT(VARCHAR(5),CONVERT(INT,@MAXNO)+1)
PRINT @MAXNO

/*3.補足固定長度方法1*/
SELECT @MAXNO=RIGHT('00000'+@MAXNO,5)
PRINT @MAXNO

/*3.補足固定長度方法2*/
SELECT @MAXNO=RIGHT(REPLICATE('0',5) +@MAXNO,5)

PRINT @MAXNO
```

{% file src="../.gitbook/assets/sql-server-ke-cheng-zuo-ye-.docx" caption="SQL 作業" %}

{% file src="../.gitbook/assets/proc\_buy\_stock.sql" caption="作業三使用變數技巧" %}

非常自豪地批次加入流水號

{% file src="../.gitbook/assets/4.-bian-zhi-liu-shui-hao-2.sql" %}



