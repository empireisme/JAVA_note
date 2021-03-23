# JDBC包成class

## 使用CLASS做連線設定

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

MAIN方法中去看連線

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

```java
package util;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Scanner;
import com.sun.java_cup.internal.runtime.Scanner;

public class test {
	public static void main(String[] args) {
//		ConnectionUtil connutil=new ConnectionUtil();
		String SQLstr="SELECT [公司代號]\r\n"
				+ "	  ,[公司名稱]\r\n"
				+ "      ,[公司簡稱]\r\n"
				+ "      ,[外國企業註冊地國]\r\n"
				+ "      ,[產業別]\r\n"
				+ "      ,[住址]\r\n"
				+ " FROM [LABS].[dbo].[上市公司基本資料]\r\n"
				+ " where [公司簡稱]='";//左括號
		
		try {
			Connection conn=ConnectionUtil.getConnection("LABS");
			Statement stmt=conn.createStatement();
			java.util.Scanner sc=new Scanner(System.in);
			ResultSet rs=stmt.executeQuery(SQLstr+sc.nextLine()+"'");//右括號
			while(rs.next()) {
				System.out.print("公司代號"+rs.getString(1));//1代表第1行
				System.out.print("公司名稱"+rs.getString(2));
//				System.out.println(rs);
			}
			System.out.println("接收成功");
			conn.close();
			sc.close();
			System.out.println("連線關閉");
  
		}catch(SQLException e) {
			e.printStackTrace();
			
		}
	}

}

```

## INSERT data

```java
package util;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.sql.Date;
//動態，等你把問號傳給他

public class test3 {
	public static void main(String[] args) {
//		ConnectionUtil connutil=new ConnectionUtil();
		String SQLstr="INSERT INTO [dbo].[STOCK_PRICE]\r\n"
				+ "           ([SYMBOL]\r\n"
				+ "           ,[DATE]\r\n"
				+ "           ,[QTY]\r\n"
				+ "           ,[OPEN]\r\n"
				+ "           ,[HIGH]\r\n"
				+ "           ,[LOW]\r\n"
				+ "           ,[CLOSE])\r\n"
				+ "     VALUES\r\n"
				+ "           (?\r\n"
				+ "           ,?\r\n"
				+ "           ,?\r\n"
				+ "           ,?\r\n"
				+ "           ,?\r\n"
				+ "           ,?\r\n"
				+ "           ,?)";//加上問號
		
		try {
			//取得Connection物件
			Connection conn=ConnectionUtil.getConnection("labs2");
			//取得動態PreparedStatement物件
			PreparedStatement pstmt=conn.prepareStatement(SQLstr);
            //設定佔位符號的值
			pstmt.setString(1, "0050");//第一個問號
			pstmt.setDate(2, new Date(2007-1900,12,31));//第二個問號
			pstmt.setInt(3, 100);
			pstmt.setInt(4, 200);
			pstmt.setInt(5, 100);
			pstmt.setInt(6, 100);
			pstmt.setInt(7, 100);
			int i =pstmt.executeUpdate();
			System.out.println("新增了"+i+"筆");
			System.out.println("接收成功");
			conn.close();
			System.out.println("連線關閉");
		}catch(SQLException e) {
			e.printStackTrace();
			System.out.println("錯誤囉");
		}
	}

}

```

## UPDATE

```java
package util;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.sql.Date;
public class test3 {
	public static void main(String[] args) {
//		ConnectionUtil connutil=new ConnectionUtil();
		String SQLstr="UPDATE [dbo].[STOCK_PRICE]\r\n"
				+ "   SET [SYMBOL] = ?\r\n"
				+ "      ,[QTY] = ?\r\n"
				+ "      ,[OPEN] = ?\r\n"
				+ "      ,[HIGH] = ?\r\n"
				+ "      ,[LOW] = ?\r\n"
				+ "      ,[CLOSE] = ?\r\n"
				+ " WHERE DATE=?";
		
		try {
			//取得Connection物件
			Connection conn=ConnectionUtil.getConnection("labs2");
			//取得動態PreparedStatement物件
			PreparedStatement pstmt=conn.prepareStatement(SQLstr);
            //設定佔位符號的值
			pstmt.setString(1, "0087");//第一個問號
			pstmt.setInt(2, 210);//第二個問號
			pstmt.setInt(3, 100);
			pstmt.setInt(4, 150);
			pstmt.setInt(5, 584);
			pstmt.setInt(6, 453);
			pstmt.setString(7, "4909-01-31");
			int i =pstmt.executeUpdate();
			System.out.println("更正了"+i+"筆");
			System.out.println("接收成功");
			conn.close();
			System.out.println("連線關閉");
		}catch(SQLException e) {
			e.printStackTrace();
			System.out.println("錯誤囉");
		}
	}

}
```



