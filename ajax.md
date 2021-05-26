# AJAX

![](.gitbook/assets/image%20%28157%29.png)

![](.gitbook/assets/image%20%28156%29.png)

![](.gitbook/assets/image%20%28154%29.png)

![](.gitbook/assets/image%20%28155%29.png)

![](.gitbook/assets/image%20%28160%29.png)

![](.gitbook/assets/image%20%28158%29.png)

![](.gitbook/assets/image%20%28159%29.png)

![](.gitbook/assets/image%20%28164%29.png)

![](.gitbook/assets/image%20%28162%29.png)

![](.gitbook/assets/image%20%28169%29.png)

## 查詢字串

![](.gitbook/assets/image%20%28166%29.png)

![](.gitbook/assets/image%20%28170%29.png)

![](.gitbook/assets/image%20%28167%29.png)

## 問題

![](.gitbook/assets/image%20%28165%29.png)

![](.gitbook/assets/image%20%28168%29.png)

![](.gitbook/assets/image%20%28171%29.png)

## id之亂

![](.gitbook/assets/image%20%28173%29.png)

![](.gitbook/assets/image%20%28172%29.png)

![](.gitbook/assets/image%20%28175%29.png)

![](.gitbook/assets/image%20%28177%29.png)

## 靜態起始

![](.gitbook/assets/image%20%28174%29.png)

![](.gitbook/assets/image%20%28176%29.png)

{% hint style="info" %}
靜態起始區塊。\(可視為是一個沒有名子的靜態方法\) 何時執行：類別載入時，JVM會自動執行類別內的所有靜態起始區塊。 依照出現順序依序執行。 功能：設定靜態變數的初值。

static int n = 100;

static { }

static { if \(DB\_TYPE.equals\(DB\_TYPE\_MYSQL\)\) { JNDI\_DB\_NAME = JNDI\_DB\_NAME\_MY; DB\_URL = DB\_URL\_MYSQL; USERID = USERID\_MYSQL; PASSWORD = PASSWORD\_MYSQL; } else if \(DB\_TYPE.equals\(DB\_TYPE\_SQLSERVER\)\) { JNDI\_DB\_NAME = JNDI\_DB\_NAME\_MS; DB\_URL = DB\_URL\_SQLSERVER; USERID = USERID\_SQLSERVER; PASSWORD = PASSWORD\_SQLSERVER; } System.out.println\("GlobalService, JNDI\_DB\_NAME=" + JNDI\_DB\_NAME\); System.out.println\("GlobalService, DB\_URL=" + DB\_URL\); System.out.println\("GlobalService, USERID=" + USERID\); System.out.println\("GlobalService, PASSWORD=" + PASSWORD\); }
{% endhint %}



