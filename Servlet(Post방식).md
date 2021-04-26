### post방식



form을 통해 자료를 보낼때 Method가 post일때

doPost 매소드가 작동한다.



```java
protected void doPost(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		String title = request.getParameter("title");
		String cntn = request.getParameter("cntn");

		BoardVO vo = new BoardVO();
		vo.setTitle(title);
		vo.setCtnt(cntn);
    
    Database.list.add(vo);
```

post방식으로 게시판의 제목과 서버에 보낼때 request.getParameter(브라우저에 찍힌 내용을 잡을때 거의 무조건다 getParameter을 쓴다고 생각하자.)매소드를 사용하여 title, cntn를 잡고 VO로 객체화 시킨후 데이터 베이스에 넣어준다.



자, 이제 게시물을 다썼다 이제 화면이 글쓰기 게시판에 머물러 있는것 보단

리스트 화면으로 가서 잘 쓰여져 있는지 확인하는게 좋을 것이다

그럴땐 다시 포워딩 해도 좋지만 이미 list로 보내는 jsp가 놀고있으니

그걸 활용해보자

``` java
response.sendRedirect("/list");
//list로 쓩~
```



+++

한글 깨질시 

request.setCharacterEndcoding("UTF-8");