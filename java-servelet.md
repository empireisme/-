# JAVA servelet

## 安裝

下載tomcat，並且解壓縮

下載MSSQL jar 加入lib

設定MSSQL登入驗證使用SQL驗證並且更改他的權限

## 安裝

{% embed url="https://pclevinblog.pixnet.net/blog/post/314562670-%5Bapache\_tomcat%5D-eclipse-裡tomcat-安裝教學" %}

## Eclipise設定

![](.gitbook/assets/image%20%2881%29.png)

## 

## 利用form取得資訊

![](.gitbook/assets/image%20%2852%29.png)

## 

## Hellow world

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

![](.gitbook/assets/image%20%2864%29.png)

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

![](.gitbook/assets/image%20%2841%29.png)

![](.gitbook/assets/image%20%2845%29.png)

#### iE 取得檔案名稱

![](.gitbook/assets/image%20%2843%29.png)

### 多檔案上傳

![](.gitbook/assets/image%20%2847%29.png)

## 重新導向網頁

![](.gitbook/assets/image%20%2844%29.png)

## 假裝的重新導向

![](.gitbook/assets/image%20%2839%29.png)

![](.gitbook/assets/image%20%2840%29.png)

![](.gitbook/assets/image%20%2846%29.png)

![](.gitbook/assets/image%20%2849%29.png)

## 4/21MVC架構

![](.gitbook/assets/image%20%2848%29.png)

![](.gitbook/assets/image%20%2842%29.png)

![](.gitbook/assets/image%20%2853%29.png)

![](.gitbook/assets/image%20%2854%29.png)

![](.gitbook/assets/image%20%2856%29.png)

## cookie 存取

![](.gitbook/assets/image%20%2850%29.png)

![](.gitbook/assets/image%20%2851%29.png)

## Session

![](.gitbook/assets/image%20%2855%29.png)

![](.gitbook/assets/image%20%2871%29.png)

## Cookie

![](.gitbook/assets/image%20%2878%29.png)

## Session發號碼牌，取號碼牌

![](.gitbook/assets/image%20%2877%29.png)

![](.gitbook/assets/image%20%2875%29.png)

## CH10 JDBC

### SQL

![](.gitbook/assets/image%20%2865%29.png)

![](.gitbook/assets/image%20%2879%29.png)

### 大絕招，設定SA

![](.gitbook/assets/image%20%2873%29.png)

![](.gitbook/assets/image%20%2882%29.png)

### 

### code

```java
public class S01_jdbc extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void doGet(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=mike;user=kirito;password=c8763";
		try {
			Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
			Connection conn = DriverManager.getConnection(connectionUrl);

			Statement state = conn.createStatement();
			ResultSet rs = state.executeQuery("Select * from House");

			while (rs.next()) {
				System.out.println(rs.getString(1) + "," + rs.getString(2));

			}
			rs.close();
			state.close();
			conn.close();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		doGet(request, response);
	}

}
```

### JNDI，需要設定兩個XML，一個在tomcat，一個在webXML

注意還是需要JDBC的檔案

![](.gitbook/assets/image%20%2880%29.png)

![](.gitbook/assets/image%20%2870%29.png)

![](.gitbook/assets/image%20%2872%29.png)

## DAO

![](.gitbook/assets/image%20%2876%29.png)

![](.gitbook/assets/image%20%2866%29.png)

![](.gitbook/assets/image%20%2869%29.png)

![](.gitbook/assets/image%20%2874%29.png)

![](.gitbook/assets/image%20%2868%29.png)

![](.gitbook/assets/image%20%2867%29.png)

