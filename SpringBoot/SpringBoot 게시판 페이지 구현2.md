# SpringBoot 게시판 구현1(DB 연결없음)



## 1. 게시판 페이지 경로 설정

- 게시판은 일단 가지고 있던 html 파일과 css 파일로 작업을 할 것이다. 
  경로는 아래와 같이 만들고, 여기서 주시해야할 파일은 `resources/static/css/board.css` 파일과 `resources/templates/views/board/board.html`파일이다.

  ![image-20191111232058121](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EA%B2%8C%EC%8B%9C%ED%8C%90%ED%8E%98%EC%9D%B4%EC%A7%80%EA%B2%BD%EB%A1%9C.PNG)



- css파일 및 html 파일이 따로 없으면 아래의 html 코드만 사용하도록한다.
  `resources/templates/views/board/board.html`
  
  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <title>mysite</title>
      <meta http-equiv="content-type" content="text/html; charset=utf-8">
      <link href="/static/css/board.css" rel="stylesheet" type="text/css">
  </head>
  <body>
  <div id="container">
      <div id="header">
          <h1>MySite</h1>
          <ul>
              <li><a href="#">로그인</a><li>
              <li><a href="#">회원가입</a>	<li>
              <li><a href="#">회원정보수정</a><li>
              <li><a href="#">로그아웃</a><li>
              <li>jh님 안녕하세요 ^^;</li>
          </ul>
      </div>
      <div id="content">
          <div id="board">
              <form id="search_form" action="#" method="get">
                  <input type="text" id="keyword" name="keyword" value="검색어를 입력해주세요.">
                  <input type="hidden" id="showBoardNum" name="showBoardNum" value="${showBoardNum}">
                  <input type="submit" value="찾기">
              </form>
              <table class="tbl-ex">
                  <tr>
                      <th>번호</th>
                      <th>제목</th>
                      <th>글쓴이</th>
                      <th>조회수</th>
                      <th>작성일</th>
                      <th>&nbsp;</th>
                  </tr>
  
                      <tr>
                          <td>1</td>
                          <td style="text-align:left; padding-left: 20px">
                              <a href="#">안녕하세요~</a>
                          </td>
                          <td>이효리</td>
                          <td>13</td>
                          <td>2019-11-11</td>
                          <td><a href="#" class="del">삭제</a></td>
                      </tr>
  
              </table>
  
              <!-- pager 추가 -->
              <div class="pager">
                  <ul>
                          <li><a href="#">◀</a></li>
                                  <li class="selected">
                                      <a href="#">1</a>
                                  </li>
                                  <li>
                                      <a href="#">2</a>
                                  </li>
                          <li><a href="#">▶</a></li>
                  </ul>
              </div>
  
              <div class="bottom">
                  <a href="#" id="new-book">글쓰기</a>
              </div>
          </div>
      </div>
      <div id="navigation">
          <ul>
              <li><a href="#">jh</a></li>
              <li><a href="#">방명록</a></li>
              <li><a href="#">게시판</a></li>
          </ul>
      </div>
      <div id="footer">
          <p>(c)opyright 2015, 2016, 2017, 2018</p>
      </div>
  </div>
  </body>
  </html>
  ```

------



## 2. 컨트롤러 경로 매핑



- 이전에 만들었던 `com/example/practice/controller/TestController.java` 에 아래의 코드를 추가한다.

```java
// 코드중략

	@RequestMapping("/board")
    public String getBoardList(){
        return "views/board/board"; // board.html 파일 경로매핑
    }
```



------



## 3. 페이지 확인 및 css 경로설정



- 컨트롤러에 매핑해둔 url인 ` http://localhost:8088/test/board `로 접근하여 해당페이지를 확인한다.
  

  ![image-20191111233219141](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EA%B2%8C%EC%8B%9C%ED%8C%90%ED%8E%98%EC%9D%B4%EC%A7%80%EC%A0%91%EA%B7%BC.PNG)



- 위의 페이지를 보면 현재 css가 적용되지 않았기때문에 css 적용하기 위해서는 경로 매핑을 해줘야한다. 
  - 일반적인 Spring 에서는 `.xml`파일에서 리소스의 경로를 입력해줘야 했지만, spring boot에서는 
    `build.gradle` 파일에  `implementation 'org.springframework.boot:spring-boot-starter-web'` 문구를 추가하여 얻은 라이브러리가 해당 작업들을 미리 해준다. 
  - js, css, img 등과 같은 정적 파일들은 `resources/static` 폴더 하위에 두는게 기본이다. 그래서 맨위 이미지를 확인해보면 게시판을 꾸며줄 css 경로가 `resources/static/css/board.css`로 되어있다.



- 위의 html 코드 5번째 줄을 보면, 아래와 같이

  ```html
  <link href="/static/css/board.css" rel="stylesheet" type="text/css">
  ```

  css 파일 경로가 `/static/css/board.css`로 되어있다. 그런데도 css가 적용안된 페이지가 나타난다.

- 해당 css 경로를 매핑해주기위해 application.properties 파일을 아래와 같이 수정한다.

  ```java
  // AS-IS
  server.port = 8088
  
  
  // TO-BE
  server.port = 8088
  # static file path settings
  spring.mvc.static-path-pattern=/static/**
  ```

  그런 후 다시 페이지를 확인해보면, 아래와같이 css가 적용된 페이지를 확인할 수 있다.

  * 적용안되면 프로젝트 재시작 후 다시확인
    

  ![image-20191111234646434](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/css%EA%B2%BD%EB%A1%9C%EC%84%A4%EC%A0%95%ED%9B%84%ED%8E%98%EC%9D%B4%EC%A7%80.PNG)

------





------




## SpringBoot 게시판 구현3(DB 연결없음)

