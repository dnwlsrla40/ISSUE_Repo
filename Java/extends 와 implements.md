# extends와 implements

이 문제는 [java가 다중상속을 지원하지 않는 이유](https://github.com/dnwlsrla40/ISSUE_Repo/blob/master/Java/Java%EA%B0%80%20%EB%8B%A4%EC%A4%91%EC%83%81%EC%86%8D%EC%9D%B4%20%EC%95%88%EB%90%98%EB%8A%94%20%EC%9D%B4%EC%9C%A0.md)를 검색하다 나온 블로그에서 interface를 상속받는데도 implements를 사용하지 않고 extends를 사용하는 데에서 궁금증이 생겨 조사하였다.

## Extends와 implements의 차이

1. extends는 일반 클래스와 abstract클래스 상속에 사용되고, implements는 interface상속에 사용된다.

2. class가 class를 상속받을 땐 extends를 사용하고, interface가 interface를 상속받을 땐 extends를 사용한다.

3. class가 interface를 사용할 땐 implements를 써야하고 interface가 class를 상요할 땐 implements를 쓸 수 없다.

4. extends는 클래스 한 개만 상속받을 수 있다.

5. extends 자식 클래스는 부모클래스의 기능을 사용한다.

6. implements는 여러개 사용 가능하다.

7. implements는 설계 목적으로 구현 가능하다.

8. implements한 클래스는 implements의 내용을 다 사용해야합니다.


즉, 같은 타입의 상속에는 extends를 사용하고, 기본적으론 클래스 상속(구현 확장) 일 경우 extends, 설계 구현일 경우 implements를 사용하는 것 같다.