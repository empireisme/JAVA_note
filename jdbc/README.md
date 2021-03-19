# JDBC

## 概述

現在分成六個步驟

1. 引入JDBCdriver
2. 註冊JDBCdriver
3. 建立起一個連線
4. 執行SQL連線
5. 從結果集得到資料
6. 清理環境

{% file src="../.gitbook/assets/sqljdbc\_9.2.1.0\_cht.zip" caption="MS SQL DRIVER" %}

## 1.JDBC的引入

下載上面的檔案到你喜歡的位置後

![&#x5728;&#x5C08;&#x6848;&#x53F3;&#x9375;&#x5F8C;](../.gitbook/assets/image%20%2813%29.png)

![](../.gitbook/assets/image%20%2816%29.png)

大膽的按下開啟不要怕!

## 2.JDBC的註冊

其實現在都不需要了，會自動註冊

![](../.gitbook/assets/xie-qu-.png)

在裡面可以找這串文字

```java
com.microsoft.sqlserver.jdbc.SQLServerDriver
```

把它貼在這裡

第一種註冊方式

```java
package day1;

public class jdbcdemo {
	public static void main(String[] args) {
		try {
		Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
		   System.out.println("OK"); 
		}catch( ClassNotFoundException e   ) {
			e.printStackTrace();
		}
		
		
	}

}
```

第二種註冊方式

```java
package day1;

import java.sql.Driver;
import java.sql.DriverManager;
import java.util.Enumeration;
import java.util.Iterator;

public class JDBCexample2 {
	public static void main(String[] args) {
		
		System.setProperty("jdbc.drivers","com.microsoft.sqlserver.jdbc.SQLServerDriver:com.mysql.cj.jdbc.Driver");
//		DriverManger.registerDriver( new Driver);
		Enumeration<Driver> e=DriverManager.getDrivers();
		Iterator<Driver> it =e.asIterator();
		it.forEachRemaining(System.out::println);
	}
}
```

## 3.連接

```java
package day1;

import java.sql.DriverManager;
import java.sql.SQLException;

public class conndemo {
	public static void main(String[] args) {
		String MSSQLurl="jdbc:sqlserver://localhost:1433;databaseName=LABS";
//		String MySQLurl="  "+" "
		try {
			DriverManager.getConnection(MSSQLurl);
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
	}

}
```

![&#x8981;&#x5728;SQL&#x505A;&#x7684;&#x8A2D;&#x5B9A;](../.gitbook/assets/image%20%2818%29.png)

## 要在MSSSQL做的設定

### MSSQL confige 當中開啟TCPIP連線

並且建立新的使用者和密碼使用SQL驗證登錄

### 在MSSQL server management 當中這樣設定

![&#x5728;&#x60F3;&#x8981;&#x7684;&#x8CC7;&#x6599;&#x5EAB;&#x7576;&#x4E2D;&#x505A;&#x9019;&#x4EF6;&#x4E8B;](../.gitbook/assets/image%20%2814%29.png)

![&#x5728;&#x4E00;&#x822C; &#x64C1;&#x6709;&#x8005;&#x7D50;&#x69CB; &#x6210;&#x54E1;&#x8CC7;&#x683C; &#x90FD;&#x8A2D;&#x5B9A;&#x6210;db owner](../.gitbook/assets/image%20%2815%29.png)

```java
package day1;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class conndemo {
	public static void main(String[] args) {
		String MSSQLurl="jdbc:sqlserver://localhost:1433;databaseName=LABS";
//		String MySQLurl="  "+" "
		String user="mike";
		String password="c8763";
		
		try {
			Connection conn=DriverManager.getConnection(MSSQLurl,user,password);
			System.out.println("OK");  
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
	}
```

drivermanager是類別名稱，靜態方法是getConnection，故可以類別.方法直接使用

![&#x8A18;&#x5F97;&#x8981;&#x91CB;&#x653E;](../.gitbook/assets/image%20%2817%29.png)

