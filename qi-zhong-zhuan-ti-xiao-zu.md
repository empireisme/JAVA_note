# 期中專題小組

## 有用的stackoverflow

{% embed url="https://stackoverflow.com/questions/5003142/show-jdbc-resultset-in-html-in-jsp-page-using-mvc-and-dao-pattern" %}

{% embed url="https://stackoverflow.com/questions/30849694/java-servlet-get-parameters-with-same-name" %}

{% embed url="https://stackoverflow.com/questions/5096454/easy-way-of-populating-javabeans-based-on-request-parameters" %}

{% embed url="https://gist.github.com/TakeOver5/cd5aa78cfec7b35122c70c6044f81976" %}

{% embed url="https://stackoverflow.com/questions/32551415/how-to-insert-arraylist-data-to-the-database" %}



菜單提交的bug

```markup
<!DOCTYPE html>
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <title>05eventBinding</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <h1>新增菜單</h1>
    <div class="container">
        <form>
        <table id="idtable" class="table table-bordered table-sm" contenteditable='true'>
            <thead>
                <tr>
                    <th scope="col">品名</th>
                    <th scope="col">價錢</th>
                    <th scope="col">介紹</th>
                    <th scope="col">功能</th>
                </tr>
            </thead>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
        </table>
        <input class="btn btn-primary" type="button" value="add row" id="buttonAdd">
        <input class="btn btn-primary" type="submit"  value="提交" />
    </form>
        
    </div>

  


    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.0/jquery.min.js"></script>
    <script>
        //測試看看
        //按下刪除按鈕(class名稱是btn-danger)時,可以將那一筆資料刪除
        //再試試看
        //按下[add row]按鈕多新增幾筆資料
        //針對新增出來的資料,按下刪除按鈕(class名稱是btn-danger)時,還可以將那一筆資料刪除嗎???
        // $('.btn-danger').click(function () {
        //     //$(this).parent().parent().remove();
        //     // $(this).parents('tr').remove(); 
        //     $(this).closest("tr").remove();        
        // });   


        //練習使用on繫結網頁上刪除按鈕，完成刪除動作
        //此時新增的還不能山
        //此時要用動態binding才能動
        $("#idtable").on("click", ".btn-danger", function () {
            $(this).closest("tr").remove();
        })



        $('#buttonAdd').click(function () {
            $('table').append("<tr><td>請輸入品名</td><td>請輸入價錢</td><td>請輸入介紹</td><td><a href='#' class='btn btn-danger'>刪除</a></td></tr>");
        });
    </script>
</body>

</html>
```

### 自己解決尚未驗證的bug

```markup
<!DOCTYPE html>
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <title>05eventBinding</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <h1>新增菜單</h1>
    <div class="container">
        <form>
        <table id="idtable" class="table table-bordered table-sm" contenteditable='true'>
            <thead>
                <tr>
                    <th scope="col">品名</th>
                    <th scope="col">價錢</th>
                    <th scope="col">介紹</th>
                    <th scope="col">功能</th>
                </tr>
            </thead>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
        </table>
        <input class="btn btn-primary" type="button"  value="add row" id="buttonAdd">
        <input class="btn btn-primary" type="submit"  value="提交" />
        <input class="btn btn-primary" type="button"  onclick="myFunction()" value="Submit form">
    </form>
        
    </div>


    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.0/jquery.min.js"></script>
    <script>
        $("#idtable").on("click", ".btn-danger", function () {
            $(this).closest("tr").remove();
        })



        $('#buttonAdd').click(function () {
            $('table').append("<tr><td>請輸入品名</td><td>請輸入價錢</td><td>請輸入介紹</td><td><a href='#' class='btn btn-danger'>刪除</a></td></tr>");
        });
        document.getElementById("myForm").submit();
    </script>
</body>

</html>
```

## 可以單筆輸入到database的範例

### Javabean

```java
package model.bean;

import java.io.Serializable;

public class Dish implements Serializable {

	private static final long serialVersionUID = 1L;

	private int Store_id;
	private String Dish;
	private int Price;
	private String Remarks;

	public Dish( ) {
		
	}
	public Dish(int store_id, String dish, int price, String remarks) {
		Store_id = store_id;
		Dish = dish;
		Price = price;
		Remarks = remarks;

	}

	public int getStore_id() {
		return Store_id;
	}

	public void setStore_id(int store_id) {
		Store_id = store_id;
	}

	public String getDish() {
		return Dish;
	}

	public void setDish(String dish) {
		Dish = dish;
	}

	public int getPrice() {
		return Price;
	}

	public void setPrice(int price) {
		Price = price;
	}

	public String getRemarks() {
		return Remarks;
	}

	public void setRemarks(String remarks) {
		Remarks = remarks;
	}

	public static long getSerialversionuid() {
		return serialVersionUID;
	}

}

```

### javadao

```java
package model.dao;

import java.sql.Connection;
import java.sql.PreparedStatement;

import model.bean.Dish;


public class DishDao {
	
	Connection conn;

	public DishDao(Connection conn) {
		this.conn = conn;
	}
	
	public int AddDish(Dish dishbean) throws Exception{
	
		PreparedStatement preState = conn.prepareStatement("INSERT INTO [dbo].[menu]\r\n"
				+ "           ([Store_id]\r\n"
				+ "           ,[Dish]\r\n"
				+ "           ,[Price]\r\n"
				+ "           ,[Remarks])\r\n"
				+ "     VALUES(?,?,?,?)");
	
		preState.setInt(1,dishbean.getStore_id());
		preState.setString(2,dishbean.getDish());
		preState.setInt(3,dishbean.getPrice());
		preState.setString(4,dishbean.getRemarks());
	
		int b = preState.executeUpdate();
		
		preState.close();
	
		return b;
	}
	
}
	


```

### javaservice

塞入連線以及塞入dao方法

```java
package model.service;

import java.sql.Connection;
import java.sql.DriverManager;

import model.bean.Dish;
import model.dao.DishDao;


public class AddMenuService {
	
	private Connection conn;
	
	public int doService(Dish dishbean) {
		int d =-123;
		try {
			getConn();
			DishDao dDao = new DishDao(conn);
			
			d = dDao.AddDish(dishbean);
			
			closeConn();
			
		} catch (Exception e) {

			e.printStackTrace();
		}
		return d;
		
	}
	
	
	
	private void getConn() {
		String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=NeverStarve;user=kirito;password=c8763";
		try {
			Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
			conn = DriverManager.getConnection(connectionUrl);
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

	private void closeConn() throws Exception {
		conn.close();
	}
	
}

```



### javaservlet

作為controller

```java
package controller;

import java.io.IOException;
import java.util.ArrayList;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import com.mysql.cj.x.protobuf.MysqlxDatatypes.Array;

import model.bean.Dish;
import model.service.AddMenuService;

@WebServlet("/AddDishServlet")
public class AddDishServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void doGet(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		ArrayList<Dish> diaL = new ArrayList<Dish>();
		for (int i = 0; i <= x; i++) {
			if (!(request.getParameter("storeUid" + i) == null)) {
				
				Integer Store_id = Integer.valueOf(request.getParameter("storeUid" + String.valueOf(i)));
				String Dish = request.getParameter("dishName");
				Integer Price = Integer.valueOf(request.getParameter("dishPrice"));
				String Remarks = request.getParameter("dishRemarks");
				Dish d = new Dish(Store_id, Dish, Price, Remarks);
				diaL.add(d);
				
			}
		}
		int u = new AddMenuService().doService(d);

		System.out.println(u);
//		request.setAttribute("DishDetail", u);
//		request.getRequestDispatcher("TheUserDetail.jsp").forward(request, response);
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		doGet(request, response);
	}

}

```



