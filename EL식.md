# EL식

```java
${키.(객체의)멤버필드명} //=request.getAttribute("키"),<&=클래스.매소드%> 를 같이써야하는데 위에 한줄로 한방에 받아줄수 있음 키값 일치의 주의
//request.setAttribute("키",객체)
```

무조건 pagecontext,request,session,application set Atttribute로 담겨져 있는거만

찍을수 있다. 자바의 변수찍어내는게 아니다!!!!!!!!!!!!!!!!!!!

***같은 이름으로 다른값이 넣고 EL식으로 찍는다면pagecontext,request,session,application순으로 위에서 하나만 찍힌다.

```java
pagaContext.setAttribute("name","A");
request.setAttribute("name","b");
session.setAttribute("name","c");
application.setAttribute("name","d");

=> ${name} = A 출력
    
 구분하려면
    ${pageContext.name}Pagetext안에 있는 키값 name의 데이터
```

***쿼리스트링에서 담겨있는애 찍을땐

```java
쿼리 : ?no=0 //no=키
받을땐 ${para.no} 로쓴다.
    
?no=0&age=10
 ${para.no},${para.age}
```

