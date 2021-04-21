# JAVA servelet

## heloo

```java
package ch3.servletbegin;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/AA")
public class MyServlet02 extends HttpServlet {
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		PrintWriter out =resp.getWriter();
		out.write("hello");
		out.close();
		
	}
}
```

![](.gitbook/assets/image%20%2836%29.png)

![](.gitbook/assets/image%20%2835%29.png)

![](.gitbook/assets/image%20%2837%29.png)

## 利用XML更改初始參數，讓廠商可以不用動到程式碼修改

![](.gitbook/assets/image%20%2829%29.png)

![](.gitbook/assets/image%20%2833%29.png)

![](.gitbook/assets/image%20%2832%29.png)

![](.gitbook/assets/image%20%2830%29.png)

![](.gitbook/assets/image%20%2834%29.png)

## servlet context

![](.gitbook/assets/image%20%2831%29.png)

## sync and sleep

```java
package ch5.ServletLifeCycle;

import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class S01_testinit
 */
@WebServlet(value="/S03_testinit2",loadOnStartup=5)
public class S03_testinit2 extends HttpServlet {
	private static final long serialVersionUID = 1L;
    
	int count=0;
	
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		synchronized(this) {
			int localcount=++count;
		}
		try {
			Thread.sleep(2000);
		}catch(InterruptedException e) {
			e.printStackTrace();
		}
		
		
		response.getWriter().write("count"+count);
		response.getWriter().close();
		
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}
	
	@Override
	public void destroy() {
		System.out.println("destroy");
		
	}

}

```

## 4/21檔案上傳

### html

![](.gitbook/assets/image%20%2838%29.png)

### Javaservlet 

![](.gitbook/assets/image%20%2839%29.png)

![](.gitbook/assets/image%20%2842%29.png)

#### iE 取得檔案名稱

![](.gitbook/assets/image%20%2840%29.png)

### 多檔案上傳

![](.gitbook/assets/image%20%2843%29.png)

## 重新導向網頁

![](.gitbook/assets/image%20%2841%29.png)

