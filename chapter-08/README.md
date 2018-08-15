## 8.SQL 쿼리 실행

직접 SQL 을 사용할 수도 있습니다.

예제:

```Go
sql := "select * from userinfo"
results, err := engine.Query(sql)
```
