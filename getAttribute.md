# getAttribute

jsp가 Servlet으로 부터  자료를 받기위해

Servlet이 Java로부터 자료를 받기위해 쓴다.

getAttribute는 setAttribute한 데이터를 가져온다

get-set 한묶음

getAttribute는 데이터값을 Object로 반환한다.

즉, 원하는 형변환이 필수. 애가 바보라서 자동 형변환이 아니라 무조건 object빼내기 때문

```java
=(원하는형)request.getAttridute("데이터명")
    //데이터명으로 데이터를 받겠다
```





# getParameter

Servlet이 jsp 로부터 자료를 받기 위해쓴다

혹은, 쿼리스트링 중 특정 값을 받아 오고 싶다 .("키")

받아온값은 String이다.

브라우저~써블릿 으로부터 jsp까지 먼길올때

HTML으로 부터 넘어오기때문에 JSP와 Servlet둘다 사용가능





```java
.getParameter("키,jsp안 name")
    
```

<img src="C:\Users\heck_\Desktop\Spring\Til\2.png">

Servlet이 JSP으로부터 자료를 받을때만 getParameter을 쓴다고 생각하자





*** forward 가 Servlet이랑 jsp와의 연동(쌍방X Servlet이 일방적으로 뿌리라고 하는 관계)이다면

get과set은 DB와 jsp의 연동이다

db가 jsp에게 직접 값을 전달할 수 없으므로 Servelt을 통해 전달하게 되는데

jsp이 getAttribute("데이터명")로 값을 요청하고 Servlet이 중간다리에서

setAttribute("get이 지정한명",DB안 원하는값)으로 db에 저장되어 있는 값을 뽑아온다.

```java
getAttribute("명");
setAttribute("get명",특정값);
get명으로 특정값을 저장한다. 그값을 get으로 불러온다.
```

