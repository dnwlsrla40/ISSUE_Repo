# Web Scope 관련 Issue

목차  
[1. Scope 사용 시 주의 사항](#Scope-사용-시-주의-사항)

## Scope 사용 시 주의 사항

각 객체의 이름.getAttribute()로 변수를 가져와 후에 가공을 한다고 하더라도 다시 이름.setAttribute()를 하지 않으면 객체 내의 변수는 변하지 않는다.

```
ApplicationScope01.java (Servlet)의 doGet 코드 내용
// value 값을 1로 세팅

protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html; charset=UTF-8");
		
		PrintWriter out = response.getWriter();
		
		ServletContext application = getServletContext();
		
		int value = 1;
		application.setAttribute("value",  value);
		
		out.println("<h1>value :" + value +"</h1><br>");
	}
```

```
ApplicationScope02.java (Servlet)의 doGet 코드 내용
// value를 가져와 값 증가

protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html; charset=UTF-8");
		
		PrintWriter out = response.getWriter();
		ServletContext application = getServletContext();
		try {
			int value = (int)application.getAttribute("value")+1;
			
			out.println("<h1>value : " + value + "</h1><br>");
		}catch(NullPointerException e) {
			out.print("value 값이 설정되지 않았습니다.");
		}
	}
```

위 코드를 실행한 후 ApplicationScope02를 여러번 로드해도 value의 값은 여전히 1이다.