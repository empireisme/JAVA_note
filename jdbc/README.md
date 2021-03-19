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



