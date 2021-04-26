# JSP

## 調派請求

![](.gitbook/assets/image%20%2891%29.png)

![](.gitbook/assets/image%20%2890%29.png)

![](.gitbook/assets/image%20%2886%29.png)

![](.gitbook/assets/image%20%2883%29.png)

![](.gitbook/assets/image%20%2884%29.png)

## Controller

```javascript
package section01;

import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


@WebServlet("/S01_getStringForAction")
public class S01_getStringForAction extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void doGet(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		User u = new User();
		u.setName("mike");
		u.setAge("18");
		request.setAttribute("myU", u);
		request.getRequestDispatcher("section01/J02_Action.jsp").forward(request, response);

	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		doGet(request, response);
	}

}

```

## View

```javascript
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>

<jsp:useBean id="myU" class="section01.User"
 scope="request"></jsp:useBean>
<%=myU.getName() %><br/>
<%=myU.getAge() %>


</body>
</html>
```

## Model

```javascript
package section01;

import java.io.Serializable;

public class User implements Serializable {
	
	private String name;
	private String age;
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getAge() {
		return age;
	}
	public void setAge(String age) {
		this.age = age;
	}
	
	
	
}

```

![](.gitbook/assets/image%20%2889%29.png)

![](.gitbook/assets/image%20%2887%29.png)

![](.gitbook/assets/image%20%2885%29.png)

![](.gitbook/assets/image%20%2888%29.png)

