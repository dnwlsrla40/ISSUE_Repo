## Log4j 관련 Test 문제

목차  
[1. Log4j 버전 관련](#org.apache.log4j.logger-cannot-be-resolved-to-a-type)

## **org.apache.log4j.Logger cannot be resolved to a type**


maven에서 log4j를 사용하다가 org.apache.log4j.Logger cannot be resolved to a type이라는 에러가 발생하였다.

이 에러는 log4j 1.2.15와 1.2.17을 사용할 경우 발생을 하는데 eclipse에서 spring mvc project 사용 시 기본으로 제공하는 log4j 설정이 1.2.15로 되어 문제가 발생하는 듯하다.

해결 방법으로는 JCL의 Facade Framework인 slf4j를 사용하면 적절한 log4j를 연결해주기 때문에 해결된다.

```
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
    <version>1.7.5</version>
</dependency>
```

나 같은 경우에는 위의 slf4j가 사용 중이었지만 버전이 낮아서 안되었는지 1.7.5 버전으로 고치니 적상작동 하였다.