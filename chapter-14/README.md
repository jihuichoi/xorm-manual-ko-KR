# xorm tools

xorm tools 는 데이터베이스 작업과 관련된 도구 모음입니다.

## 실행 파일 설치

[got](https://github.com/gobuild/got) 가 설치되어 있으면, got 를 이용해 설치할 수 있습니다.
```
got go-xorm/cmd/xorm
```

또는 [gobuild](http://gobuild.io/download/github.com/lunny/got) 에서 내려받을 수 있습니다.

## 소스 설치

`go get github.com/go-xorm/cmd/xorm`

상황에 따라 다음 패키지들을 같이 설치할 수 있습니다.

* github.com/go-xorm/xorm

* Mysql: [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql)

* MyMysql: [github.com/ziutek/mymysql/godrv](https://github.com/ziutek/mymysql/godrv)

* Postgres: [github.com/lib/pq](https://github.com/lib/pq)

* SQLite: [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3) 

** sqlite 를 사용하려면 `go build -tags sqlite3` 명령을 이용해 빌드를 해야 합니다.

## 명령

아래와 같은 명령을 사용할 수 있습니다.

* **reverse**     데이터베이스 구조를 코드로 변환
* **shell**       모든 데이터베이스에서 사용할 수 있는 일반 쉘
* **dump**        데이터베이스의 모든 테이블 구조체를 표준출력으로 내보냄
* **source**      표준 입력으로 sql 실행
* **driver**      지원하는 모든 드라이버 목록 표시

## Reverse

Reverse 명령은 데이터베이스 구조를 구조체나 클래스로 변환하는 도구입니다. 도구를 설치한 뒤

`xorm help reverse`

를 통해 도움말을 볼 수 있습니다.

예제:

sqlite:
`xorm reverse sqite3 test.db templates/goxorm`

mysql:
`xorm reverse mysql root:@/xorm_test?charset=utf8 templates/goxorm`

mymysql:
`xorm reverse mymysql xorm_test2/root/ templates/goxorm`

postgres:
`xorm reverse postgres "dbname=xorm_test sslmode=disable" templates/goxorm`

위 명령을 실행하면 `./model` 디렉토리에 go 파일이 생성됩니다.ectory

#### 서식 파일과 설정

xorm 은 go 와 c++ 을 지원하며 go, goxorm, c++ 용 기본 서식 파일을 지원합니다. 서식 파일 디렉토리에 서식 파일 생성에 관련된 설정 파일을 추가할 수 있습니다.

````
lang=go
genJson=1
```

lang 은 go 와 c++ 만 가능합니다.
genJson 은 1이나 0을 사용할 수 있으며, 1이면 구조체에 json 태그를 포함시킵니다.

## Shell

Shell 명령은 데이터베이스 동작과 관련된 도구입니다. 예를 들어 테이블을 생성하거나 변경, 데이터를 삽입하거나 삭제하는 동작들을 실행할 수 있습니다.

예를 들어 `xorm shell sqlite3 test.db` 명령은 sqlite3 데이터베이스에 접속합니다. 쉘에서 `help` 명령을 통해 쉘 명령 목록을 볼 수 있습니다.

## Dump

Dump 명령은 모든 데이터베이스 구조와 데이터를 SQL 구문 형태로 표준 출력으로 내보냅니다.\

예를 들어 `xorm dump sqlite3 test.db` 명령은 sqlite3 test.db 데이터베이스의 구조와 데이터를 표준 출력으로 내보냅니다. 이를 파일로 저장하려면 다음과 같이 사용합니다. `xorm dump sqlite3 test.db > test.sql`

## Source

`xorm source sqlite3 test.db < test.sql` 명령을 사용하면 test.db 에 sql 파일을 실행할 수 있습니다.

## Driver

지원하는 모든 드라이버 목록을 표시합니다. sqlite3 는 기본으로 지원하지는 않습니다.

## 저작권

 BSD License
 [http://creativecommons.org/licenses/BSD/](http://creativecommons.org/licenses/BSD/)
