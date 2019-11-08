# SpringBoot port 번호 변경 후 적용



- src\main\resources\application.properties에 server.port = 8088과 같이 작성 후 저장한다.
  * window key + R 누른후 "cmd" 입력 + Enter 하여 command 창에서  "**netstat -ano**" 명령어 입력 후 확인하여 사용하지 않는 포트를 server.port에 입력

![image-20191028212118502](https://github.com/Yujaehyeong/SpringBoot-with-IntelliJ/blob/master/%EC%9D%B4%EB%AF%B8%EC%A7%80/springboot/port%EB%B3%80%EA%B2%BD.PNG?raw=true)

- 다시 실행해본다.
- 포트적용이 안되는 경우 목록중에 Build > Build Project를 누른후 다시 실행한다.
- 그래도 안되면 Reimport Gradle Project를 실행하고 다시 프로젝트를 실행한다.

### 