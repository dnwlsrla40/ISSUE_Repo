# Oracle 관련 Error

목차  
[1. logon denied Error](#oracle-invalid-username/password;logon-denied-error)

## Oracle invalid username/password;logon denied Error

오라클을 이용해서 DB에 접속하려고 하던 중 이클립스에서 위와 같은 에러가 발생하였다.

SQL developer에서 user를 새로 등록해주었는데도 이러한 문제가 발생하였다.

![Error Picture](./Images/SQL/Invalid_username_Error.JPG)

구글링에서 나온 방법은 cmd창으로 SQL developer 계정을 만들어 접속하는 방법이었다. 아래처럼 해보니 제대로 되었다.


```
C:\Users\user> sqlplus "/as sysdba"

SQL> create user "계정 이름" identified by "비밀번호";

SQL> grant 권한(connect, resource, dba) to "계정 이름"
```

![Error Picture](./Images/SQL/Invalid_username_Error2.JPG)