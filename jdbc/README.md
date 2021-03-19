# JDBC

{% file src="../.gitbook/assets/sqljdbc\_9.2.1.0\_cht.zip" caption="MS SQL DRIVER" %}

## JDBC的部署

## JDBC的註冊

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

## 連接

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

![&#x8981;&#x5728;SQL&#x505A;&#x7684;&#x8A2D;&#x5B9A;](../.gitbook/assets/image%20%2815%29.png)

## 要在MSSSQL做的設定

MSSQL confige 當中開啟TCPIP連線

在

![&#x5728;&#x60F3;&#x8981;&#x7684;&#x8CC7;&#x6599;&#x5EAB;&#x7576;&#x4E2D;&#x505A;&#x9019;&#x4EF6;&#x4E8B;](../.gitbook/assets/image%20%2813%29.png)

![&#x5728;&#x4E00;&#x822C; &#x64C1;&#x6709;&#x8005;&#x7D50;&#x69CB; &#x6210;&#x54E1;&#x8CC7;&#x683C; &#x90FD;&#x8A2D;&#x5B9A;&#x6210;db owner](../.gitbook/assets/image%20%2814%29.png)

