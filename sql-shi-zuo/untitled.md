# SQL stored procedure

SQL stored procedure

```sql
declare @Rate decimal(20,4)
exec PR_GetPrice '2020/1/1','twd',@Rate output
print @Rate 

CREATE PROCEDURE [PR_GetPrice]
@Date	date,--匯率日期
@Cur	varchar(3),--幣別
@Rate	decimal(20,4) output--匯率
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	SELECT @Rate=0--初始值
	SELECT @Rate=RATE FROM EXCHANGE
	WHERE [DATE]=@Date AND CUR=@Cur
END
GO


```

利用declare 來執行

```sql
exec PR_GetPrices '2019/1/2'

/*
EXEC PR_GetPrices '2019/1/2'
*/
-- =============================================
-- Author:		colin
-- Create date: 2020.8.1
-- Description:	回傳匯率資料
-- =============================================
ALTER PROCEDURE [dbo].[PR_GetPrices]
@Date	date--匯率日期
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	SELECT * FROM EXCHANGE
	WHERE [DATE]=@Date 
END
```



