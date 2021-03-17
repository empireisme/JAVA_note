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

