# 期中專題code

## 連線設定用的class

```java
package iii_project;

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

## ITEM

```java
package iii_project;

import java.util.Arrays;

public class Item {
	String isImage;
    String success;
    String id;
	ItemType[] data;
	
	public String getIsImage() {
		return isImage;
	}

	public void setIsImage(String isImage) {
		this.isImage = isImage;
	}

	public String getSuccess() {
		return success;
	}

	public void setSuccess(String success) {
		this.success = success;
	}

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public ItemType[] getData() {
		return data;
	}

	public void setData(ItemType[] data) {
		this.data = data;
	}

	@Override
	public String toString() {
		return "Item [isImage=" + isImage + ", success=" + success + ", id=" + id + ", data="
				+ Arrays.toString(data) + "]";
	}
    
}
```

## ITemtype

```java
package iii_project;

public class ItemType {
	private int seq;
	private String 資料年度;
	private String 統計項目;
	private String 稅目別;
	private String 資料單位;
	private String 值;
	
    public int getSeq() {
		return seq;
	}

	public void setSeq(int seq) {
		this.seq = seq;
	}

	public String get資料年度() {
		return 資料年度;
	}

	public void set資料年度(String 資料年度) {
		this.資料年度 = 資料年度;
	}

	public String get統計項目() {
		return 統計項目;
	}

	public void set統計項目(String 統計項目) {
		this.統計項目 = 統計項目;
	}

	public String get稅目別() {
		return 稅目別;
	}

	public void set稅目別(String 稅目別) {
		this.稅目別 = 稅目別;
	}

	public String get資料單位() {
		return 資料單位;
	}

	public void set資料單位(String 資料單位) {
		this.資料單位 = 資料單位;
	}

	public String get值() {
		return 值;
	}

	public void set值(String 值) {
		this.值 = 值;
	}

	//getter and setter
	@Override
	public String toString() {
		return "ItemType [seq=" + seq + ", 資料年度=" + 資料年度 + ", 統計項目=" + 統計項目 + ", 稅目別=" + 稅目別 + ", 資料單位=" + 資料單位
				+ ", 值=" + 值 + "]";
	}
	

}

```

## mainprogram

```java
package iii_project;

import java.io.FileWriter;
//import java.io.FileWriter;
import java.io.InputStreamReader;
import java.net.URL;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

import com.google.gson.Gson;

import au.com.bytecode.opencsv.CSVWriter;

public class mainprogram {
	public static void main(String[] ignored) throws Exception {
		//get data from url to java
		URL url = new URL("https://api.kcg.gov.tw/api/service/get/2c1d9959-d038-4918-bae3-409680f8193a");
	    InputStreamReader reader = new InputStreamReader(url.openStream());
	    Item dto = new Gson().fromJson(reader, Item.class);
	    ItemType[] dd = dto.data; //get the crucial data 
	    //prepare to insert java data to mssql
		String SQLstr="INSERT INTO [dbo].[iii_project]\r\n"
				+ "           ([seq]\r\n"
				+ "           ,[資料年度]\r\n"
				+ "           ,[統計項目]\r\n"
				+ "           ,[稅目別]\r\n"
				+ "           ,[資料單位]\r\n"
				+ "           ,[值])\r\n"
				+ "     VALUES\r\n"
				+ "           (?,?,?,?,?,?)";
		Connection conn=ConnectionUtil.getConnection("labs2");
		try {
			//取得Connection物件

			PreparedStatement pstmt=conn.prepareStatement(SQLstr);
			for(int i=0;i<dd.length;i++) {
				pstmt.setInt(1, dd[i].getSeq());
				pstmt.setString(2, dd[i].get資料年度());
				pstmt.setString(3, dd[i].get統計項目());
				pstmt.setString(4, dd[i].get稅目別());
				pstmt.setString(5, dd[i].get資料單位());
				pstmt.setString(6, dd[i].get值());
				pstmt.executeUpdate();
			}
			
	
			
			
		}catch(SQLException e) {
			e.printStackTrace();
			System.out.println("錯誤囉");
		}
		//get data from mssql 
		String SQLstr2="SELECT [seq]\r\n"
				+ "      ,[資料年度]\r\n"
				+ "      ,[統計項目]\r\n"
				+ "      ,[稅目別]\r\n"
				+ "      ,[資料單位]\r\n"
				+ "      ,[值]\r\n"
				+ "  FROM [dbo].[iii_project]";
		try {
			PreparedStatement pstmt2=conn.prepareStatement(SQLstr2);
			ResultSet rs=pstmt2.executeQuery();
			System.out.printf("%-12s","seq");
			System.out.printf("%-11s","資料年度");
			System.out.printf("%-11s","統計項目");
			System.out.printf("%-12s","稅目別");
			System.out.printf("%-12s","資料單位");
			System.out.printf("%-12s","值");
			System.out.println();
//			while(rs.next()) {
//				System.out.printf("%-12s",rs.getInt(1));
//				System.out.printf("%-12s",rs.getString(2));
//				System.out.printf("%-12s",rs.getString(3));
//				System.out.printf("%-12s",rs.getString(4));
//				System.out.printf("%-12s",rs.getString(5));
//				System.out.printf("%-12s",rs.getString(6));
//				System.out.println();
//			} //要特別注意如果用寫入的話不能打印出來不然會寫入空包彈
			CSVWriter writer = new CSVWriter(new FileWriter("D:\\LABS\\result.csv"));
			writer.writeAll(rs, true);	
		}
		catch(Exception e){
			e.printStackTrace();

		}
		conn.close();
		System.out.println("連線關閉");
		
	}
}
```

{% hint style="info" %}
要特別注意如果用寫入的話不能打印出來不然會寫入空白
{% endhint %}

