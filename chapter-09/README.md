## 9. SQL 명령 실행

insert, update, delete 등의 SQL 명령을 실행하려면 Exec 메서드를 사용합니다.

```Go
sql = "update userinfo set username=? where id=?"
res, err := engine.Exec(sql, "xiaolun", 1) 
```
