
Xorm 은 Go 언어용으로 개발된 단순하지만 강력한 ORM 도구입니다.

# 기능

* Struct <-> Table 매핑 지원

* 체이닝(Chainable) APIs

* 트랜잭션 지원

* 원시 SQL 동작 지원

* 데이터베이스 스키마 동기화 지원

* 쿼리 캐시를 이용한 속도 향상

* 데이터베이스 리버스 지원, [Xorm Tool README](https://github.com/go-xorm/cmd/blob/master/README.md) 참조

* 단순 케스케이드 불러오기 지원

* 낙관적(Optimistic) 잠금 지원


# 지원하는 DB 드라이버 목록

현재 지원하는 데이터베이스/sql Go 패키지 드라이버 <sup>FIXME!</sup>
<!-- FIXME: Drivers for Go's sql package which currently support database/sql includes: -->

* Mysql: [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql)

* MyMysql: [github.com/ziutek/mymysql/godrv](https://github.com/ziutek/mymysql/godrv)

* Postgres: [github.com/lib/pq](https://github.com/lib/pq)

* Tidb: [github.com/pingcap/tidb](https://github.com/pingcap/tidb)

* SQLite: [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)

* MsSql: [github.com/denisenkom/go-mssqldb](https://github.com/denisenkom/go-mssqldb)

* MsSql: [github.com/lunny/godbc](https://github.com/lunny/godbc)

* Oracle: [github.com/mattn/go-oci8](https://github.com/mattn/go-oci8) (실험적 지원)

* ql: [github.com/cznic/ql](https://github.com/cznic/ql) (실험적 지원)

# 설치

[gopm](https://github.com/gpmgo/gopm) 을 설치한 경우

	gopm get github.com/go-xorm/xorm

아니면

	go get github.com/go-xorm/xorm

# 문서

* [설명서](http://xorm.io/docs)(영문)

* [설명서](tableContents.md)(한글 임시)

* [GoDoc](http://godoc.org/github.com/go-xorm/xorm)

* [GoWalker](http://gowalker.org/github.com/go-xorm/xorm)

# 토론

[Xorm on Google Groups](https://groups.google.com/forum/#!forum/xorm) 를 이용하세요.

# 기여

기여를 하려면 [CONTRIBUTING](https://github.com/go-xorm/xorm/blob/master/CONTRIBUTING.md) 페이지를 참고하세요.

# 저작권

 BSD License
 [http://creativecommons.org/licenses/BSD/](http://creativecommons.org/licenses/BSD/)
