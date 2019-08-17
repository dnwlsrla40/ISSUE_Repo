# MySQL 관련 Error

목차  
[1. 테이블 생성 에러](#테이블-생성-에러)

## 테이블 생성 에러

Error Code: 1046 No database selected Select the default DB to be used by double-clicking its name in the SCHEMAS list in the sidebar.

### 발생 원인

MySQL Workbench에서 테이블을 생성할 때 발생  
어떤 DB에 테이블을 만들지 지정해주지 않았기 때문에 발생

### 해결

DB이름을 입력해줘서, 그 안에 테이블을 만들 수 있도록 해줘야한다.

ex)
```
create table DB이름.test(
    tno int,
    title varchar(50)
);
```

이 방법은 매번 DB명을 써줘야 해 번거롭다.


또 다른 방법으로는 DB를 선택하여 기본 스키마로 잡아주는 것이다.

테이블을 생성할 DB를 더블클릭하거나 마우스 오른쪽 버튼으로 'Set as Default Schema'로 Default 스키마로 설정해 주는 것이다.

![테이블 생성 에러](/Images/SQL/MySQL/테이블생성에러.JPG)

**Command Line 방법**

MySQL Command Line에서 DB에 권한을 주는 방법은 다음과 같다.

Mysql>
grant all privileges on 데이터베이스명.* to 유저아이디@localhost identified by '비밀번호';