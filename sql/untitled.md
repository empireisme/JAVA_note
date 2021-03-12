# 基礎SQL\(CRUD\)

## SQL

SQL的核心語法結構為

```sql
use 資料庫名稱
SELECT 欄位名A,欄位名B
FROM 表名
WHERE 條件

```

## SQL插入的語法

```sql
use LeonPower;

Select * From House;

Select * From Product;

Insert Into Product(productname, productprice, productdate) Values('blueberry', 99, '2021/03/09');

Select * From Product;

Insert Into Product(productname, productprice, productdate) 
Values('nb', 24900, '2025-12-31'), ('drink', 70, '2021-03-09'), ('food', 100, '2021-04-01');

Select * From Product;
```

## SQL更改語法

```sql
update employee set salary=35000 where eid=3;

Select * From Employee;

使用別的資料庫來改

Update employee set salary= promotelist.promotesalary from promotelist
where employee.eid=promotelist.eid;

```

## SQL刪除語法

```sql
delete from employee where eid=9 and ename='michelle';
```

## SQL查詢

```sql
Select FirstName as Name,hiredate,gender,maritalStatus
From DimEmployee
select title from dimemployee;
select distinct title from dimemployee;


Select FirstName ,hiredate,gender,maritalStatus
From DimEmployee
where MaritalStatus='S' and Gender='M'


Select FirstName ,hiredate,gender,maritalStatus
From DimEmployee
where MaritalStatus='M' and Gender='F'
```

## 把NULL關掉

```sql
set ANSI_NULLS OFF
Select Name,Productnumber,weight,listprice

From Production.Product

where Weight=NULL;


Select Name,Productnumber,weight,listprice

From Production.Product

where Weight is not NULL
```

## 新增名字長度的欄位

```sql
use AdventureWorksDW2019;

SELECT Firstname ,LEN(FiRSTNAME) as name_length,HireDATE,title
,getdate()as mydate
from DimEmployee
```

```sql
use AdventureWorks2019;

SELECT NAME,Length=DATALENGTH(NAME),Len(NAME) as Len1,ProductNumber,ListPrice,Weight,Color
from Production.product
Order by name
```

NAME是欄位名，然後把創造一個欄位名稱叫做LENGTH裡面存DATALENGTH\(NAME\)

## PARSE 轉換

```sql
PARSE(string_value as data_type[using culture]) 
```



```sql
Select PARSE ('$34,567'as money using 'en-US') as usdollar1;
--Select PARSE ('$34,567'as money using 'zh-TW') as usdollar2;

Select PARSE ('NT$34,567'as money using 'zh-TW') as ntdollar2
```

## 利用TRY語法即使輸入錯誤，也會回傳NULL

```sql
SELECT TRY_CAST('20211210' as date ) as result1;
```

```sql
SELECT TRY_PARSE('12/10/2021' as datetime using 'en-US');
```

