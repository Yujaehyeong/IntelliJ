# SpringBoot 게시판 구현(DB 연결없음)



### 1. 기본페이지 생성 

- 게시판구현을 할 때 **Thymeleaf** 템플릿 엔진을 사용할것이다. (아래내용 참고)****

  > [Thymeleaf 이야기]: https://github.com/ihoneymon/spring-boot-orm-learn/blob/master/THYMELEAF_TEMPLATE_ENGINE.md#thymeleaf-%EC%9D%B4%EC%95%BC%EA%B8%B0



- 설명을 생략하고 바로 적용하는 방법으로 들어가 보겠다. 
  아래 링크에 정리가 잘되어있어서 그대로 따라하면 된다.

  > [프로젝트에 Thymeleaf 적용]: https://github.com/ihoneymon/spring-boot-orm-learn/blob/master/THYMELEAF_TEMPLATE_ENGINE.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-thymeleaf-%EC%A0%81%EC%9A%A9



- 설명된 것과 같이 build.gradle 파일에 해당 문구를 추가하겠다.

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

  

- 그런다음  `src/main/resources/template`  하위에 `index`라는 디렉토리를 하나 더 만들 것이다.