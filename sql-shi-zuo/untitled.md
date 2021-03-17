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

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		colin
-- Create date: 2021.3.17
-- Description:	買進股票
-- =============================================
/*
DECLARE @ERRMSG	VARCHAR(1000)
EXEC PROC_BUY_STOCK '2020/8/14',2330,'585H1234567',1000,@ERRMSG OUTPUT
PRINT @ERRMSG
SELECT * FROM STOCK_DEAL
*/
ALTER PROCEDURE PROC_BUY_STOCK
@DATE date,--交易日期
@SYMBOL	varchar(10),--股票代號
@TDCCACCOUNT	varchar(20),--集保帳號
@QTY	decimal(20,4),--買進量
@ERRMSG	varchar(1000) output--錯誤訊息
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	IF NOT EXISTS(SELECT * FROM STOCK_NAME WHERE SYMBOL=@SYMBOL)
	BEGIN
		SELECT @ERRMSG='股票代號不存在'
		RETURN;
	END;

	--取得最大序號
	DECLARE @MAXNO	VARCHAR(20)
	DECLARE @SERIAL VARCHAR(20)
	SELECT @MAXNO=ISNULL(MAX(SERIAL),'190001010000') FROM STOCK_DEAL
	SELECT @MAXNO=CONVERT(VARCHAR(20),CONVERT(INT,RIGHT(@MAXNO,4))+1)
	SELECT @MAXNO=RIGHT('0000'+@MAXNO,4)
	SELECT @SERIAL=CONVERT(VARCHAR(10),@DATE,112)+@MAXNO
	--取得股票開盤價格
	DECLARE @PRICE DECIMAL(20,4)
	SELECT @PRICE=[OPEN]
	FROM STOCK_PRICE
	WHERE DATE=@DATE AND SYMBOL=@SYMBOL
		--藥補的
	BEGIN TRAN
	BEGIN TRY
		INSERT STOCK_DEAL --insert到DEAL
		(
		SERIAL,DATE,SYMBOL,TDCCACCOUNT,DATATYPE,
		QTY,PRICE,AMT,FEE,TAX,
		TOTALAMT,
		LOGDATE
		)
		SELECT @SERIAL AS SERIAL,@DATE AS [DATE],@SYMBOL AS SYMBOL,@TDCCACCOUNT AS TDCCACCOUNT,1 AS DATATYPE,
		@QTY AS QTY,@PRICE AS PRICE,ROUND(@PRICE*@QTY,0) AS AMT,ROUND(@PRICE*@QTY*0.01,0) AS FEE,ROUND(@PRICE*@QTY*0.003,0) AS TAX,
		ROUND(@PRICE*@QTY,0)+ROUND(@PRICE*@QTY*0.01,0)+ROUND(@PRICE*@QTY*0.003,0) AS TOTALAMT,
		GETDATE() AS LOGDATE


		COMMIT
	END TRY
	BEGIN CATCH
		ROLLBACK
		SELECT @ERRMSG=ERROR_MESSAGE()
	END CATCH
END
GO
```

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		colin
-- Create date: 2021.3.17
-- Description:	買進股票
-- =============================================
/*
DECLARE @ERRMSG	VARCHAR(1000)
EXEC PROC_BUY_STOCK '2020/8/14',2330,'585H1234567',1000,@ERRMSG OUTPUT
PRINT @ERRMSG
SELECT * FROM STOCK_DEAL
*/
create or alter PROCEDURE PROC_BUY_STOCK
--先交代參數
@DATE date,--交易日期
@SYMBOL	varchar(10),--股票代號
@TDCCACCOUNT	varchar(20),--集保帳號
@QTY	decimal(20,4),--買進量
@ERRMSG	varchar(1000) output--錯誤訊息
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	IF NOT EXISTS(SELECT * FROM STOCK_NAME_FULL WHERE SYMBOL=@SYMBOL)
	BEGIN
		SELECT @ERRMSG='股票代號不存在'
		RETURN;
	END;

	--取得最大序號
	DECLARE @MAXNO	VARCHAR(20)
	DECLARE @SERIAL VARCHAR(20)
	SELECT @MAXNO=ISNULL(MAX(SERIAL),'190001010000') FROM STOCK_DEAL
	SELECT @MAXNO=CONVERT(VARCHAR(20),CONVERT(INT,RIGHT(@MAXNO,4))+1)
	SELECT @MAXNO=RIGHT('0000'+@MAXNO,4)
	SELECT @SERIAL=CONVERT(VARCHAR(10),@DATE,112)+@MAXNO
	--取得股票開盤價格
	DECLARE @PRICE DECIMAL(20,4)
	SELECT @PRICE=[OPEN]
	FROM STOCK_PRICE
	WHERE DATE=@DATE AND SYMBOL=@SYMBOL
		--藥補的
	IF NOT EXISTS(SELECT [OPEN] FROM STOCK_PRICE WHERE  DATE=@DATE and SYMBOL=@SYMBOL    )
	BEGIN
		SELECT @ERRMSG='無價格訊息'
		RETURN;
	END;

	BEGIN TRAN
	BEGIN TRY
		INSERT STOCK_DEAL --insert到DEAL
		(
		SERIAL,DATE,SYMBOL,TDCCACCOUNT,DATATYPE,
		QTY,PRICE,AMT,FEE,TAX,
		TOTALAMT,
		LOGDATE
		)
		SELECT @SERIAL AS SERIAL,@DATE AS [DATE],@SYMBOL AS SYMBOL,@TDCCACCOUNT AS TDCCACCOUNT,1 AS DATATYPE,
		@QTY AS QTY,@PRICE AS PRICE,ROUND(@PRICE*@QTY,0) AS AMT,

		Case when ROUND(@PRICE*@QTY,0) <=100000 then  ROUND(@PRICE*@QTY*0.001,0)
		else ROUND(@PRICE*@QTY*0.005,0) END AS FEE,

		ROUND(@PRICE*@QTY*0.003,0) AS TAX,
		ROUND(@PRICE*@QTY,0)+
		Case when ROUND(@PRICE*@QTY,0) <=100000 then  ROUND(@PRICE*@QTY*0.001,0)
		else ROUND(@PRICE*@QTY*0.005,0) END
		+ROUND(@PRICE*@QTY*0.003,0) AS TOTALAMT,
		GETDATE() AS LOGDATE
```

