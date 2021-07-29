# 面試問題

## 中華系統開發

物件三大特性 

各種join

如何做join效能才比較好\(by index\)

如果甚麼都沒寫會是甚麼\(friend\)

如何去做sub query

private protect 差在哪

spring和spring mvc差在哪

JQUERY如何傳送資料到後端

JDBC的流程為何?\(prepared statement那些\)

## fizzbuzz Rcode

```text
vec <- rnorm(9)
index <- c(3,6,7)
number <- c(23,10,3)

  for(i in 1:length(index)){
    vec[index[i]]=number[i]
  }

vec
```

```text
1類別(Class):描述物件的建構方式，為抽象的概念，含有物件的屬性及功能。
 物件(Object):照類別的描述所建構出實體。
2.封裝(Encapsulation)
優點:能防止資料受外界不當存取，避免造成不可預期後果。

缺點:被private宣告的方法屬性不能在外部類別使用，取值和設定值需要使用getter/setter。

3.繼承對於封裝的影響:
若要使用父類別中private的參數，需要使用父類別繼承下來的public方法才行。

4.多型的意義:不同物件執行相同方法時，可以得到不同的結果。
優點:同樣名稱的方法，可以因應賦予身分的不同而有適當做法。
```

