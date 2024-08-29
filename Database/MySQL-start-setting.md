# MySQL 개발 환경 세팅

> mysql이 설치되어 있어야 함

### 1. 서버 실행

```bash
mysql.server start

Starting MySQL..
SUCCESS!
```

### 2. 비밀번호 설정

```bash
mysql_secure_installation
```

- 위의 명령어를 입력하면 이제 비밀번호와 각종 설정을 시작함

```bash
VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough.

Would you like to setup VALIDATE PASSWORD component?
Press y|Y for Yes, any other key for No
```

- 비밀번호 복잡도 검사에 대한 거임
- y 누른 후에 너무 복잡하면 못 외울 거 같아서 Low(0)로 설정했음

```bash
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No)
```

- 익명의 사용자 삭제할 것인지?
- y 선택함

```bash
Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No)
```

- root 계정을 원격(외부)에서의 접속을 차단할 것인지?
- 당연히 y

```bash
By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.

Remove test database and access to it? (Press y|Y for Yes, any other key for No)
```

- 테스트 데이터베이스 삭제할 것인지?
- 새로 만들거 예정이라 필요 없어서 y 함

```bash
Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No)
```

- 변경사항 즉시 적용할 것인지?
- 당연히 y

### 3. 제대로 동작하는지 테스트

- `mysql -u root -p` 를 입력한 후, 방금 설정한 비밀번호 입력하기

```bash
mysql >
```

- 이런 식으로 변한 거 확인 되면 정상적으로 동작하는 거임

```bash
mysql > create database DB이름;
```

- DB 정상적으로 생기는 거 확인하면 다음처럼 종료하면 됨

```bash
mysql > exit

~ % mysql.server stop
```

---

> 참고 자료

[homebrew를 이용한 mysql 설치 및 세팅 방법](https://programmerjoon.tistory.com/23)

[mysql 설치, 삭제, 서버 관련 명령어](https://velog.io/@cataiden/mysqlcommand)

[mysql 테이블 만들기](https://blog.naver.com/pjok1122/221539169731)
