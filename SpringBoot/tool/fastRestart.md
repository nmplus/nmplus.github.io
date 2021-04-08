## 데몬 재기동없이 Build 후 반영

- spring-boot는 Tomcat의 라이브러리를 내장하고 있어 daemon기동으로 8080포트(default)롤 기동 할 수 있다. 그런데 정적소스(html등)를 수정 할때에도 재기동이 필요하다. java소스나 정적소스를 수정후 Build만으로 화면에 반영되도록 spring-boot는 개발도구를 제공한다.

- eclipse의 경우 Auto Build설정(default)으로 파일을 저장만 하는 행위로 build가되고  
IntelliJ는 Build > Build Project를 해줘야 build를 진행한다.

- spring-boot-devtools
  - spring-boot-devtools을 사용할경우 build만으로도 재기동이 되므로 개발환경 설정시 필히 추가하도록한다.
  - IntelliJ는 Build Project를 Ctrl + S 단축키로 변경시 이클립스와 동일한 효과를 얻을수있다.
    (File > Save All 단축키가 Ctrl + S를 사용중이기 때문에 이를 삭제 후 적용한다. 수정위치는 Shift 2번 > Keymap > Main Menu)

- Gradle  
```
    dependencies {
        developmentOnly("org.springframework.boot:spring-boot-devtools")
    }
```
- Maven   
```
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <optional>true</optional>
        </dependency>
    </dependencies>
```
- 가이드문서
  https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using-boot-devtools