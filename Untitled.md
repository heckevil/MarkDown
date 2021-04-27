# 게시판만들기

1. list - severlet (for문으로 뿌리기)
2. write - servlet 
3. boardVO - 글양식
4. Database - Arraylist();
5. detali - servlet 
6. Del 삭제
7. mod 수정

*****

* 고용 = list,write (굳이 각각 ~번 글 ~번글 작성 안하고 공용으로 써서

  리스트를 만든다.)

그외 각각 개인 게시물 No안에서 사용

~번 글 디테일

~번 글 수정

~번 글 삭제



* Form 이있다면 트리거는 필수 method가 post일땐 글번호도 전송

get방식은 url창에 글번호 <%=no%>를 적지만

post방식은 안적어 주기떄문에 직접 전송

```html
<form active="/~" method="post">
    <input type="hidden" name="no" value="<%=no%>">
    <input type="submit" value="~">
</form>
```

