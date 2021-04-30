#  커넥션 하는법 (DB)

* DbUtils

```java
//데이터 베이스 연결도구


class static Connection getCon() Throws Exception{
    final String DB_NAME = "boardver3"; //연결할 db테이블 이름
    final String DRIVER = "com.mysql.cj.jdbc.Driver";
    //아파치 라이브러리 com.mysql.cj.jdbc.Driver
    final String URL="jdbc:mysql://localhost:3308/boardver3";
    //jdbc:mysql://localhost:DB포트번호/테이블명
    final String USER_NAME = "DBID";
    final String PASSWARD = "DBPASSWARD";
    Class.forName(Driver);
    //=클래스로더 라는 녀석을 통해서 해당 데이터베이스 드라이버를 로드
Connection con=
    DriverManager.getConnection(URL,USER_DRIVER,PASSWARD);
	return con;
} //DB_name,Driver,URL,User_name,passward 멤버필드 적용

//연결기라고 생각하자. 로그인 연결기. 접속기


public static void close (Connection con, PreparedStatement ps){
    close(con,ps,null);
} 

public static void close(Connection con, PreparedStatement ps, ResultSet rs){
    if(rs != null){
        try{
            rs.close();
        } catch(SQLExecption e) {
            	e.printStackTrace();
        }
    }
    
    if(ps != null){
        try{
            rs.close();
        } catch {SQLException e}{
            e.printStrackTrace();
        }
    }
    
    if(con != null){
        try{
            con.close();
        } catch (SQLExecption e){
            e.printStackTrace();
        }
    }
 //커넥터? 오픈 순서 con, ps, rs순 but 닫을땐 rs, ps, con
 //나누는 이유 : 묶여있다가 하나 에러터지만 다안 닫힌다.
}


//con = db랑 연결 통로, ps = 적어놓은 쿼리를 실행, rs= 모든 실행 결과문들의 모음

```



# BoardBAO

* Data Access Object(DB담당)

```java
public class BoardBAO{
	//글등록 write.jsp에서 post로 보내면 Servlet에서 BoardBAO.insertBoard(vo); 으로 등록
	public static int insertBoard(BoardVO3 vo){
        Connection con = Null; 
        preparedStatement  ps = Null; //Prepared!!
        
        String sql = "INSERT INTO t_board"
            		+"(title,ctnt)"
            		+"VALUES"
            		+"(?,?)";
        try{
           con = DbUtils.getCon();
            ps = con.prepareStatement(sql); //prepare!!
        	ps.setString(1, vo.getTitle()); //(정수번째, 값) 정수번째 ?에 값을 넣겠다.
            								// 1번째 ?에 title, 2번째 ctnt
            ps.setString(2, vo.getCtnt());
            return ps.executeUpdate(); //영향받은 행수 리턴. Update는 대게 1뜸 그외 오류
        }catch(Exception e){ 
            e.printStackTrace();
        }finally {
            DbUtils.close(con, ps);
        }
        return 0;
    }
    
    public static List<BoardVO3> selBoardList(){
        //List<BoardVO3> list = BoardBAO.selBoardList();
        //request.setAttribute("list", list); board 넣은거 받아서 뿌리기
        List<BoardVO> list = new ArrayList();
        Connection con = null;
        PreparedStatement = null;
        ResultSet rs =null;
        
        String sql ="INSERT i_board, title, regdt FROM t_board";
        
        try{
            con =DbUtils.getCon();
            ps.prepareStatement(sql);
            //쿼리문 select는 무조건 executeQuery
            rs = ps.executeQuery();
            //날린 쿼리문으로 받은 데이터를 결과로 모음
        	
            while(rs.next())
            //rs.next(); 최초무조건 실행 1번줄 가리킴 레코드가 있는지 확인-> add(vo)해줌 add하게 없으면 안함. 그럼 next때 없으니 false나와서 빠져나옴 true면 또 추가
            {
                BoardVO vo = new BoardVO();
                list.add(vo);
                
                int iboard = rs.getInt("iboard");
                String title = rs.getString("title");
                String regdt = rs.getstring("regdt");
                
                vo.setIboard(iboard);
                vo.setTitle(title);
                vo.setRegdt(regdt);
            }
        
        }catch(Exception e){
            e.printStackTrace();
        }finally{
            DbuTils.close(con,ps,rs);
        }
        return list;
        
        
    }
    


```