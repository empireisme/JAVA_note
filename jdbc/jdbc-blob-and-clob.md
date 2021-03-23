---
description: 如何把圖片放入資料夾
---

# JDBC BLOB and CLOB

## BLOB

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

