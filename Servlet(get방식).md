# Servlet

웹에서 받은 신호를 받기 위해서 사용

요청한 신호를 뿌릴때는 .jsp파일을 사용한다.



### Get, Post

Get: 서버에게 요청 보낼때 주소에게 적어서 보냄.

​			같은 주소를 날렸을 때 다른 화면을 뿌릴 수 있다

​			@Overriding 사용



Post: 서버에게 요청 보낼때 주소에게 적지 않고 숨겨서 보냄.

​			로그인 등 개인정보 => ?~ 커리스트링



### Flam work

- 제3자가 메소드를 요청

응답을 할때 문자열 방식으로 ("") 응답을 한다, 그리고 그 문자열안에

HTML태그가 있다.

```javascript
//get 방식
protected void doGet(HttpServletRequest request, HttpServletResponse response)

/*특정 ip로 받은 요청들은 request로 들어가고
그에 대한 반은은 response 발송*/
```





### 리스폰방식

서블렛으로 요청 하면 숨겨져있던 jsp을 내보냈는것으로 주로 사용한다

```java
//jsp로 응답하는법
protected void doGet(HttpServletRequest request, HttpServletResponse response)

String jsp = "jsp파일 위치";
RequestDispather 변수명 = request.getRequestDispatcher(jsp);
변수명.forward(request,response);


==> request.getRequestDispatcher(jsp).forward(request, response); 로 줄여 쓸 수 있다.위 코드를 상용 하면 
```

@WebServlet("/주소")를 get방식으로 요청할때 주소안 jsp파일로 응답하게 

된다.





## 쿼리스트링(Query String)

1. GET방식으로 서버 요청(request)을 보낼 때 같이 보내는 data

   ```html
   
   ?로 시작
   
   구분: &
   
   구성: 키=값
   //getParameter = name=("값") 둘이 연결된다. 꼭 name이여야함!
   
   
   Ex)이름,나이 정보를 보낸다. (서버에서 원한다.)
   
   주소?name=홍길동&age=20
   <!-- 키(key)와 밸류(Value)로만 나뉘어져 있어서 순서도 상관X
   		주소?age=20&name=홍길동 -->
   
   list.jsp 안 get방식
   href="/detail?no=<%=i%>"
   ```





2. 자료를 받아서 입력할때

   주소창에 /주소?name=홍길동&age=20 으로 주소에  요청할 것이다.

``` java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		String name = request.getParameter("name");
		String age = request.getParameter("age");
				
		System.out.println("name : "+name);
		System.out.println("age : "+age);}
```

doget 파라미터와 throws 뒤에 코드는 신경 쓸필요는 없다

중요한건 메소드안 변수와 프린트 식.

요청된 name과 age를 문자열로 만들어 저장하고 프린트한다.

대충 이런식으로 메커니즘이 있다고 생각하면된다.



*request.Parameter로 받은 값들은 모두 String으로 받아드린다

정수로 받아도 문자열로 인식한다.



3. jsp에서도 쿼리스트링에 받은 값을 출력할 수 있다.

```java
//서블렛의 request랑 불러올 jsp의 request, 포워딩될 request는 같은 주소값이다. 즉 서로 불러오거나 입력될 수 있다..

@WebServlet("/list3")
protected void doGet(HttpServletRequest request, HttpServletResponse response)
    
@Forwarding
RequestDispatcher rd = request.getRequestDispatcher(jsp);
rd.forward(request, response);

@jsp
<%
String name = request.getParameter("name");
String age = request.getParameter("age");
%>

//모두 같은 request    
```



*** 별첨

써블렛으로 주소를 요청 받아서(request) jsp로 그 결과를 뿌리는데

주소를 요청할때 A태그로 요청하는 경우가 있다.

A태그 ''<a href=주소>''는 클릭했을때 주소값으로 날라간다고 생각하지만,

주소값을 주소창에 직접 넣어준다고 생각해야한다.

http:를 인식하며 http:가 붙었을땐 기존 주소창에 있는 주소를 지우고 전체 입력, 없다면 그 글자만 현제 주소창에서 추가 입력해준다.