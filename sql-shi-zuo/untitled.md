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

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

/*
EXEC PR_CalcuUsdPrice '2019/1/2','2019/1/10'
*/
-- =============================================
-- Author:		colin
-- Create date: 2020.8.1
-- Description:	計算美金股價
-- =============================================
ALTER PROCEDURE PR_CalcuUsdPrice
@DateS	date,--計算日期起
@DateE	date--計算日期迄
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	/*宣告計算暫存檔*/
	DECLARE @TB TABLE
	(
		SYMBOL	VARCHAR(10),--股票代號
		[DATE]	DATE,--日期
		AMOUNT	DECIMAL(18,6),--美金收盤價
		[CLOSE]	DECIMAL(18,6),--收盤價
		PRIMARY KEY(SYMBOL,[DATE])
	)

	DECLARE @RATE	TABLE
	(
		[DATE] DATE,
		[RATE] DECIMAL(20,5)
	)

	/*新增匯率日期*/
	INSERT @RATE 
	(
	[DATE],[RATE]
	)
	SELECT [DATE],0 AS [RATE] FROM STOCK_PRICE WHERE [DATE] BETWEEN @DateS AND @DateE GROUP BY [DATE]

	/*取得台幣換算成美金匯率*/
	UPDATE @RATE SET RATE=dbo.FN_GetExchange([DATE],'TWD','USD',2)

	/*新增計算資料*/
	INSERT @TB 
	(
		SYMBOL,[DATE],AMOUNT,[CLOSE]
	)
	SELECT SYMBOL,[DATE],AMOUNT,[CLOSE]
	FROM STOCK_PRICE
	WHERE [DATE] BETWEEN @DateS AND @DateE
	
	/*計算美金價格*/
	UPDATE @TB SET AMOUNT=ROUND([CLOSE]*B.RATE,2)
	FROM @TB A INNER JOIN @RATE B ON A.[DATE]=B.[DATE]

	--SELECT * FROM @TB
	--SELECT * FROM @RATE
	--RETURN

	BEGIN TRY
		/*開始進行交易*/
		BEGIN TRAN
			UPDATE STOCK_PRICE SET AMOUNT=B.AMOUNT
			FROM STOCK_PRICE A INNER JOIN @TB B ON A.SYMBOL=B.SYMBOL AND A.[DATE]=B.[DATE]
		COMMIT
	END TRY
	BEGIN CATCH
		/*更新失敗,回滾資料*/
		ROLLBACK TRAN
		PRINT '儲存失敗:'+ERROR_MESSAGE()
	END CATCH

END
GO
```



