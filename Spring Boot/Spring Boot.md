# Spring Boot 관련 Error

목차  
[1. driver class Error](#failed-to-determine-a-suitable-driver-class-error)

## Failed to determine a suitable driver class error

Spring Boot는 어플리케이션이 시작될 때 필요한 기본 설정들을 자동으로 설정하게 되어있는데, 그 중 DataSource 설정이 자동 설정 될 때 필요한 데이터베이스 정보가 설정되지 않아서 발생하는 문제

```
Description:

Failed to configure a DataSource:'url' attribute is not specified and no embedded datasource could be configured.

Reason: Failed to determine a suitable driver class

Action:

Consider the following:
  If you want an embedded database (H2,HSQL or Derby), please put it on the classpath.
  If you have database settings to be loaded from a particular profile you may need to activate it(no profiles are currently active).
```

프로젝트가 생성될 때 application.properties 파일이 자동 생성되었으나 빈파일로 되어있는데, 여기에 사용자가 원하는 DB설정을 넣고, 맞는 드라이버와 라이브러리 설치, JDBC 설정을 해줘야 한다.

만약 JDBC 설정이 필요없고 어떤 DB를 사용할 지 정하지 않았다면 메인 클래스에 아래의 어노테이션을 추가하면 된다.

```
@SpringBootApplication
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```