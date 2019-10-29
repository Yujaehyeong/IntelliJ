# IntelliJ Gradle 프로젝트 생성



#### 1. Gradle 프로젝트 생성

File > New > Project 경로를 따라 아래와 같이 선택 후 Next 선택

![image-20191028211805820](https://github.com/Yujaehyeong/IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/intelliJ/gradle%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%83%9D%EC%84%B1%20%EA%B2%BD%EB%A1%9C.PNG?raw=true)

![image-20191028212118502](https://github.com/Yujaehyeong/IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/intelliJ/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%83%9D%EC%84%B1%20%EC%84%A4%EC%A0%95.PNG?raw=true)


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

#### 2. 프로젝트 생성

Finish를 누르면 프로젝트가 생성된다. 생성된 프로젝트의 디렉토리 구조는 아래와 같다.
(main과 test 디렉토리가 생성됨)

![image-20191029215449876](https://github.com/Yujaehyeong/IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/intelliJ/gralde%20%ED%8F%B4%EB%8D%94%EA%B5%AC%EC%A1%B0.PNG?raw=true)
