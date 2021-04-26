# request

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response)
    request.getRequestDispatcher(jsp).forward(request, 	      response);//servlet 
    
string no = request.getParameter("no"); //get방식

<% String no = request.getParameter("no"); %> //jsp
    
servlet에서 forward을 했기 때문에 servlet에서 request은 get방식에서 특정값 을 받아 논 변수를 jsp가서 그대로 쓸 수 있다. 같은값이다.
```

