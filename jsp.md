# JSP

## 調派請求

![](.gitbook/assets/image%20%2897%29.png)

![](.gitbook/assets/image%20%2895%29.png)

![](.gitbook/assets/image%20%2888%29.png)

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

![](.gitbook/assets/image%20%2894%29.png)

![](.gitbook/assets/image%20%2889%29.png)

![](.gitbook/assets/image%20%2887%29.png)

![](.gitbook/assets/image%20%2892%29.png)

![](.gitbook/assets/image%20%2885%29.png)

![](.gitbook/assets/image%20%2891%29.png)

![](.gitbook/assets/image%20%2886%29.png)

![](.gitbook/assets/image%20%2896%29.png)

![](.gitbook/assets/image%20%2893%29.png)

![](.gitbook/assets/image%20%2890%29.png)

![](.gitbook/assets/image%20%2898%29.png)

![](.gitbook/assets/image%20%28100%29.png)

![](.gitbook/assets/image%20%2899%29.png)

```javascript
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>${userDetail.userName}</title>
</head>
<body>

<table border="1">
<tr>
<th>使用者ID</th>
<th>使用者名稱</th>
<th>使用者密碼</th>
</tr>

<tr>
<td>${userDetail.userId}</td>
<td>${userDetail.userName}</td>
<td>${userDetail.password}</td>
</tr>

</table>

</body>
</html>
```



![](.gitbook/assets/image%20%28101%29.png)

![](.gitbook/assets/image%20%28105%29.png)

## Filter

![](.gitbook/assets/image%20%28104%29.png)

在Filter

![](.gitbook/assets/image%20%28102%29.png)

![](.gitbook/assets/image%20%28106%29.png)

## 完整範例架構

### JAVA端

1. select.jsp\(前端查詢表單\)
2. GetOneUserServlet\(Controller\)
3. GetOneUserService\(Model\)
4. UsersDao\(Model\)
5. UserDetail.jsp\(View\)經過渲染的
6. Users\(Model\)bean配合MSSQL

### 設定MSSQL



東西是成對的

![](.gitbook/assets/image%20%28103%29.png)

![](.gitbook/assets/image%20%28107%29.png)

![](.gitbook/assets/image%20%28108%29.png)

{% file src=".gitbook/assets/javamvc3333.zip" %}

