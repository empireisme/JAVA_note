# Untitled

## 子分類裡面最高價

```sql
select Max(listprice)
from production.product
group by product.productsubcategoryID\
```

```sql

select name,listprice
from production.product
where listprice>=all(select max(listprice) as subcategorymaxprice
from production.product
group by product.productsubcategoryID);
```

