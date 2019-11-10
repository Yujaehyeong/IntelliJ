# SpringBoot Port 변경



### 1. Gradle 프로젝트 생성

- ##### File > New > Project 를 선택하고 아래 순서를 따른다.

  | ![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%83%9D%EC%84%B11.PNG) |
  | ------------------------------------------------------------ |
  | ![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%83%9D%EC%84%B12.PNG) |
  | ![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%83%9D%EC%84%B13.PNG) |
  | ![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%83%9D%EC%84%B14.PNG) |
  | ![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%83%9D%EC%84%B15.PNG) |
  
  2번째 사진참조
  
  - GroupId
    - 자신의 프로젝트를 고유하게 식별하게 해 주는 것
    - package 명명 규칙을 따른다.
  - ArtifactId?
    - 제품의 이름으로, 버전 정보를 생략한 jar 파일.
    - 프로젝트 이름과 동일하게 설정.
    - 소문자로만 작성함. 특수문자는 사용 x
  - Version?
    - SNAPSHOT: 개발용, RELEASE: 배포용
    - 숫자와 점을 사용하여 버전 형태를 표현(1.0, 1.1, 1.0.1 등)



------




## 2. 프로젝트 실행 

- ##### Run 버튼(or Ctrl + F11)을 눌러서 프로젝트를 실행한다.

- ##### 실행도중 아래와 같은 오류가 나면 아래링크를 참조한다.

  ![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/port%EC%98%A4%EB%A5%98.PNG?raw=true)

  * [포트번호 수정 후 적용]: https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%98%A4%EB%A5%98%EC%88%98%EC%A0%95/SpringBoot%20port%20%EB%B3%80%EA%B2%BD%20%ED%9B%84%20%EC%A0%81%EC%9A%A9.md

- ##### 이상없이 실행이 되면 브라우저에서 localhost:8088로 접근한다.

![image-20191104231529841](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20url%20%EC%A0%91%EA%B7%BC%EC%98%A4%EB%A5%981.PNG)


- ##### 위와같이 에러페이지가 뜨는 경우 메세지 그대로 매핑된 경로가 없기때문에 연결을 하라는 것이다.
  
##### 아래 사진과 같이 com.example. practice 패키지 밑에 contoller 패키지를 생성한후 Controller로 사용할 Class를 생성한다.

  ![image-20191105223555242](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EA%B8%B0%EB%B3%B8%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC%EC%83%9D%EC%84%B1.PNG?raw=true)


- ##### 클래스 생성 후 아래의 코드를 작성한다.

  

```java
package com.example.practice.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController // 컨트롤러를 명시하는 어노테이션
@RequestMapping("/test") // url 경로설정 //localhost:8088/test로 접근
public class TestController {

    @RequestMapping("/test") // localhostL8088/test/test로 접근
    public String getRequest(){
        return "Hello SpringBoot!!"; // 해당 경로로 요청이 들어오면 문자열 형태 그대로 반환
    }

}
```



- ##### 다시 프로젝트를 실행하고 브라우저에서 설정된 경로인 localhost:8088/test/test로 접근한다.
  

 ![image-20191105223555242](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/%EA%B8%B0%EB%B3%B8%EA%B2%BD%EB%A1%9C%EC%84%A4%EC%A0%95%ED%8E%98%EC%9D%B4%EC%A7%80.PNG?raw=true)

- ##### 위와 같은 페이지가 나오는 것을 확인 할 수 있다.
  



## 다음순서: SpringBoot 게시판 구현(DB 연결없음)

> https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/SpringBoot/SpringBoot%20%EA%B2%8C%EC%8B%9C%ED%8C%90%20%ED%8E%98%EC%9D%B4%EC%A7%80%20%EA%B5%AC%ED%98%84.md#springboot-%EA%B2%8C%EC%8B%9C%ED%8C%90-%EA%B5%AC%ED%98%84db-%EC%97%B0%EA%B2%B0%EC%97%86%EC%9D%8C