# Untitled

## 連線class

```text
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

```text
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

```text
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

```text
package iii_project;

import java.io.InputStreamReader;
import java.net.URL;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import com.google.gson.Gson;

public class mainprogram {
	public static void main(String[] ignored) throws Exception {
		URL url = new URL("https://api.kcg.gov.tw/api/service/get/2c1d9959-d038-4918-bae3-409680f8193a");
	    InputStreamReader reader = new InputStreamReader(url.openStream());
	    Item dto = new Gson().fromJson(reader, Item.class);
	    ItemType[] dd = dto.data;
//		System.out.println(dd.length);
		String SQLstr="INSERT INTO [dbo].[iii_project]\r\n"
				+ "           ([seq]\r\n"
				+ "           ,[資料年度]\r\n"
				+ "           ,[統計項目]\r\n"
				+ "           ,[稅目別]\r\n"
				+ "           ,[資料單位]\r\n"
				+ "           ,[值])\r\n"
				+ "     VALUES\r\n"
				+ "           (?,?,?,?,?,?)";
		try {
			//取得Connection物件
			Connection conn=ConnectionUtil.getConnection("labs2");
			PreparedStatement pstmt=conn.prepareStatement(SQLstr);
			pstmt.setInt(1, dd[0].getSeq());//第一個問號
			pstmt.setString(2, dd[0].get資料年度());
			pstmt.setString(3, dd[0].get統計項目());
			pstmt.setString(4, dd[0].get稅目別());
			pstmt.setString(5, dd[0].get資料單位());
			pstmt.setString(6, dd[0].get值());
			pstmt.executeUpdate();
			conn.close();
			System.out.println("連線關閉");
		}catch(SQLException e) {
			e.printStackTrace();
			System.out.println("錯誤囉");
		}
	}
}
```



