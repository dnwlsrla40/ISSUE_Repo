### @Enumerated의 기본값 EnumType.ORDINAL 사용 시 문제점

@Enumerated의 기본값인 EnumType.ORDINAL 사용 시 문제점이 있다. 아래는 enum class RoleType이다.

```
public enum RoleType {
    USER, ADMIN
}
```

RoleType에는 USER와 ADMIN이 있다. 이를 @Enumerated의 기본 속성인 EnumType.ORDINAL을 이용해서 MEMBER를 등록하면 
DB에는 USER와 ADMIN이 순서대로 0과 1로 저장된다.
실제로 table create시 SQL도 integer 타입으로 실행된다.

```
// Member Entity
@Enumerated
private RoleType roleType;

//JpaMain
Member member = new Member();
member.setId(1L);
member.setUsername("A");
member.setRoleType(RoleType.USER);

em.persist(member);

tx.commit();
```

![Memeber Table Create](/images/CREATE_MEMBER_TABLE.PNG)

![DB 결과](/images/ORDINAL_DB.PNG)

여기서 RoleType에 후에 GUEST를 추가하게 되고 이를 0번으로 하고싶어 아래와 같이 수정을 한다고 해보자.

```
public enum RoleType {
    GUEST, USER, ADMIN
}
```

그리고 이 GUEST를 이용해서 3번째 데이터인 C를 INSERT하자.

```
Member member = new Member();
member.setId(3L);
member.setUsername("C");
member.setRoleType(RoleType.GUEST);

em.persist(member);

tx.commit();
```

![DB 결과](/images/ORDINAL_문제점.PNG)

C는 GUEST인 0으로 재대로 들어갔다. 하지만 문제는 A도 0번인 채로 그대로 남아있다. B 역시 현재 1번은 USER지만 우리가 원한 값은 ADMIN이다. 
DB는 A,B 데이터는 변경된 것이 없기 때문에 그대로 인것이다. 이처럼 ORDINAL 옵션으로 사용하면 이러한 문제점이 발생하여 잘 사용하지 않는다.