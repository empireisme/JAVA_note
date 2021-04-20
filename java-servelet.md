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

