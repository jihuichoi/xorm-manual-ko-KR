## 7. 레코드 삭제하기

하나 이상의 레코드를 삭제합니다.

* id 로 삭제

```Go
err := engine.Id(1).Delete(&User{})
```

* 다른 조건을 이용하여 삭제

```Go
err := engine.Delete(&User{Name:"xlw"})
```
