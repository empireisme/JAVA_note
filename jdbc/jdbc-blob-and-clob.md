---
description: 如何把圖片放入資料夾
---

# JDBC BLOB and CLOB

## 把圖片放入資料庫

1. 先放SQL指令
2. FileinputStream
3. connection設定
4. preparedstmt
5. fin conn close
6. 記得用Try catch 包住

```java
package util;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class testblob {

	public static void main(String[] args){
		String SQLstr="INSERT INTO [dbo].[MyFile_Table]"
				+ "([FileName]"
				+ " ,[File])"
				+ "VALUES"
				+ "(?,?)";//two ?? 
		//provide index 1 and 2 
		
		try {
			FileInputStream fin=new FileInputStream("pic/html.png");
			String fileName="html.png";
			Connection conn = ConnectionUtil.getConnection("LABS");
			PreparedStatement pstmt=conn.prepareStatement(SQLstr);
			
			pstmt.setString(1, fileName);
			pstmt.setBinaryStream(2, fin);// jdbc part finished
			
			int i=pstmt.executeUpdate();
	
			fin.close();
			conn.close();
			
			System.out.println("寫入完成"+i+"筆");
			
		} catch (SQLException | FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

	}

}

```

![](../.gitbook/assets/image%20%2820%29.png)

![](../.gitbook/assets/image%20%2819%29.png)

```java
package util;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConnectionUtil {
	private static String MSSQLurl="jdbc:sqlserver://localhost:1433;databaseName=";
//	String MySQLurl="  "+" "
	private static String user="kirito";
	private static String password="c8763";
	//start writing method
	public static Connection getConnection(String dbname) throws SQLException {//要記得throw
		String url = MSSQLurl+dbname;
		Connection conn=DriverManager.getConnection(url,user,password);
		System.out.println("連線成功");
		return conn;
	
	}

}
```

## 把圖片從資料庫拿出來放到指定資料夾

```java
package util;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
public class testblobOut {

	public static void main(String[] args){
		String SQLstr="SELECT [FileName]"
				+ ",[File]"
				+ "FROM [LABS].[dbo].[MyFile_Table]";//two ?? 
		//provide index 1 and 2 
		
		try {
			Connection conn = ConnectionUtil.getConnection("LABS");
			PreparedStatement pstmt=conn.prepareStatement(SQLstr);
			ResultSet rs = pstmt.executeQuery();
			
			while(rs.next()) {
		
				FileOutputStream fout=new FileOutputStream("pic/"+rs.getString(1));
				//constructer use to name the picture name
				InputStream in=rs.getBinaryStream(2);//from database to java
				int i;
				while((i=in.read())!=-1) {
					fout.write(i);
				}
				fout.flush();//把記憶體資料衝出去
				fout.close();
				in.close();
			
			}
			conn.close();
			
		} catch (SQLException | FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

	}

}

```

