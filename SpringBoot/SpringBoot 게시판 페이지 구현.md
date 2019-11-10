# SpringBoot 게시판 구현(DB 연결없음)



### 1. 타임리프 라이브러리 추가

- 게시판구현을 할 때 **Thymeleaf** 템플릿 엔진을 사용할것이다. (아래내용 참고)

  > https://github.com/ihoneymon/spring-boot-orm-learn/blob/master/THYMELEAF_TEMPLATE_ENGINE.md#thymeleaf-%EC%9D%B4%EC%95%BC%EA%B8%B0



- 이제 바로 적용하도록 해보자.  아래 링크에 정리가 잘되어있어서 그대로 따라하면 된다.
  
> https://github.com/ihoneymon/spring-boot-orm-learn/blob/master/THYMELEAF_TEMPLATE_ENGINE.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-thymeleaf-%EC%A0%81%EC%9A%A9

- 설명된 것과 같이 `build.gradle` 파일에 해당 문구를 추가하겠다.

  ```java
  // 코드중략
  dependencies {
      // 기존에 있던 문구들
      implementation 'org.springframework.boot:spring-boot-starter-web'
      testImplementation 'org.springframework.boot:spring-boot-starter-test'
      // 아래 문구를 추가    
      compile "org.springframework.boot:spring-boot-starter-thymeleaf"
  }
  // 코드중략
  ```



------



## 2. html 페이지 구성

-  `src/main/resources/template`  하위에 `index`라는 디렉토리를 하나 더 만들고 `index.html` 파일을 추가한다.

  ![image-20191108235356996](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/index%ED%8E%98%EC%9D%B4%EC%A7%80%EC%83%9D%EC%84%B1.PNG)

- index.html 코드

  ```html
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
  <html xmlns:th="http://www.w3.org/1999/xhtml">
  <head>
      <meta charset="UTF-8"/>
      <title>Index: ORM learning programming</title>
  </head>
  <body>
  <h1>Made by honeymon</h1>
  <div>
      <div>Very simple!</div>
      <!-- SpEl: Spring Expression Language 사용 -->
      <div th:text="${greeting}">Greeting</div>
  </div>
  </body>
  </html>
  ```



------



## 3. 컨트롤러 재구성

- `index.html` 파일 추가 후,
  이전에 만들어 두었던 `com/example/practice/controller/TestController.java` 컨트롤러를 아래처럼 수정.

  - `아래처럼 코드 수정 시, import가 자동으로 되기 때문에 그 부분은 생략함. ` 

  ```java
  // 코드중략
  
  // AS-IS
  @RestController
  @RequestMapping("/test")
  public class TestController {
  
      @RequestMapping("/test") // localhostL8088/test/test로 접근
      public String getRequest(){
          return "Hello SpringBoot!!";
      }
  }
  
  //////////////////////////////////////////////////////////////////////////////////////
  //////////////////////////////////////////////////////////////////////////////////////
  
  // 코드중략
  
  // TO-BE
  @Controller // Controller 어노테이션으로 수정
  @RequestMapping("/test")
  public class TestController {
  
      @RequestMapping("/test") // localhostL8088/test/test로 접근
      public String getRequest(Model model){ // Model 객체 파라미터 추가
          // Model 객체에 데이터 저장 - key:"greeting" | value:"Hello, world!" 
          model.addAttribute("greeting", "Hello, world!"); 
          return "index/index"; // index.html 파일 경로매핑
      }
  }
  ```



------



## 4. 페이지 확인


- 코드 수정이 완료되었다면 이전처럼 브라우저에서 `localhost:8088/test/test`로 접근한다.

  ![image-20191109002212580](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%ED%83%80%EC%9E%84%EB%A6%AC%ED%94%84%20%EA%B8%B0%EB%B3%B8%ED%99%94%EB%A9%B4%EA%B5%AC%EC%84%B1.PNG)

