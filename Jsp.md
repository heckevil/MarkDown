# Jsp

1. .jsp확장자
2. 동적 웹어플리케이션 컴포넌트 
3. jsp는 서블릿으로 변환되어 실행



## M(Model) V(View[jsp]) C(Controller)

1. 브라우저의 요청은 주소창을 거쳐 Controller(Servlet)으로 요청한다
2. 서블렛은 Model(DB)에게 파일을 요청
3. View(jsp)는 그걸 받아서 브라우저에 다시 뿌림



## Servlet

1. 브라우저가 주소창에 값을 입력하여 Servlet에게 어떤걸 요청한다.
2. 요청 값 하나하나에 대해 써블릿으로 만들어야 한다.

@WebServlet("/write")  : ("") 안에 요청값을 넣어주면 그값이 들어왔을때 해당 서블렛이 실행된다

<img src ="C:\Users\heck_\Desktop\Spring\Til/1.png"/>

## 게시판연습

1. 게시판 요건

   1. list
      * 글목록
   2. write
      * 제목(title), 내용(ctnt),글넘버(iboard)

2. 서블릿

   1. BoardListServlet

      * /list 요청이 들어왔을때 list 로보내줌

   2. BoardWriteServlet

      * /write 요청이 드어왔을때 write로 보내줌

        ```java
        request.setAttribute("data", Database.list);
        		
        		String jsp = "/WEB-INF/jsp/list.jsp";		
        		request.getRequestDispatcher(jsp).forward(request, response);
        
        //get 방식으로 통한 자료 전송(바인딩)
        ```

        

3. JSP

   1. List
   2. write

