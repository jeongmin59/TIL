# MySQL 설치 시 마주친 에러

> mac 사용 중 (homebrew)

### 1. mysql 제거가 되지 않을 때

- 개인 노트북에 회사 개발 환경이랑 똑같이 세팅하기 위해서 mysql을 설치해야 했음
- mysql을 사용한 적은 없지만 설치가 되어 있어서 깔끔하게 삭제하고 시작하려고 함
- `brew uninstall mysql` 하는 순간 다음의 에러 발생

```bash
~ % mysql --version
mysql  Ver 9.0.1 for macos12.7 on arm64 (Homebrew)

~ % brew uninstall mysql
Error: Unexpected method 'appcast' called on Cask adoptopenjdk8.
Follow the instructions here:
  https://github.com/Homebrew/homebrew-cask#reporting-bugs
```

- 다음의 명령어를 입력하면 됨

```bash
brew uninstall adoptopenjdk8
```

- 그 다음 mysql을 uninstall 했으나 여전히 `mysql --version` 을 하면 여전히 mysql이 남아있었음

- `which mysql` 하면 mysql 위치가 확인 가능

- 이전에 `mysql-client`를 설치했었는데 이거 때문에 제대로 삭제가 되지 않았음

```bash
brew uninstall mysql-client
```

- 깔끔하게 삭제된 것을 확인한 후 `brew install mysql` 해줌
- 정상적으로 재설치 완료!

### 2. mysql server 시작이 안 될 때

- 설치를 완료하고 서버를 시작하려고 하는데 다음과 같은 에러가 발생했음

```bash
~ % mysql.server start
Starting MySQL

... ERROR! The server quit without updating PID file (/opt/homebrew/var/mysql/Jeongminui-MacBookAir.local.pid).
```

- 다음의 방법으로 해결함

```bash
brew uninstall mysql

sudo rm -rf /opt/homebrew/var/mysql
sudo rm /opt/homebrew/etc/my.cnf

brew cleanup

brew install mysql
```

- 정상적으로 작동하는 것을 확인함!

---

> 참고 자료

[MySQL 완전 삭제](https://velog.io/@dhengh0205/Mysql-완전-삭제)
