# JOIN

123

```sql
select productnumber,name,
	category=case productline
		when 'R' then 'road'
		when 'M' then 'mountain'
		else 'sold out'
	end
from production.product
order by productnumber
```



## JOIN

### 下面兩種寫法得到的效果是一樣的

```sql
Select Orders.orderid, Orders.productid, Orders.orderdate, Product.productid, 
Product.productname, Product.productprice
From Orders JOIN Product
ON Orders.productid = Product.productid;

Select orderid, Orders.productid, orderdate, Product.productid, productname, productprice
From Orders JOIN Product
ON Orders.productid = Product.productid;
```

```sql
select orderid,Orders.productid,orderdate,product.productid,productname,productprice
from orders,product
where orders.productid=product.productid
```

### 也可以使用別名

```sql
Select orderid, d.productid, orderdate, p.productid, productname, productprice
From Orders as d JOIN Product as p
ON d.productid = p.productid;
```

上面是用d表示orders,用p表示product

## Right join

```sql

select orderid, d.productid, orderdate, p.productid, productname, productprice
from orders as d right join product as p
on d.productid=p.productid;
```

![](../.gitbook/assets/image%20%286%29.png)

## Cross join 

如果order有n筆資料，product有m筆資料，總共會有n\*m筆資料

```sql

select orderid, d.productid, orderdate, p.productid, productname, productprice
from orders as d cross join product as p
where d.productid=p.productid
```

注意Cross join 一定要使用 **where**

在這個例子當中cross join 結果跟inner join 一樣

