# JDBC包成class

類別

```java
package util;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConnectionUtil {
	private static String MSSQLurl="jdbc:sqlserver://localhost:1433;databaseName=LABS";
//	String MySQLurl="  "+" "
	private static String user="mike";
	private static String password="c8763";
	//start writing method
	public Connection getConnection() throws SQLException {//要記得throw
		
		Connection conn=DriverManager.getConnection(MSSQLurl,user,password);
		System.out.println("連線成功");
		return conn;
	
	}

}

```

main

```java
package util;

import java.sql.Connection;
import java.sql.SQLException;

public class test {
	public static void main(String[] args) {
		ConnectionUtil connutil=new ConnectionUtil();

		try {
			Connection conn=connutil.getConnection();
			System.out.println("接收成功");
			conn.close();
			System.out.println("連線關閉");

		}catch(SQLException e) {
			e.printStackTrace();
			
		}
	}

}

```

