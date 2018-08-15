## 이벤트
xorm 은 두 가지 이벤트를 지원합니다. 하나는 데이터 모델 구조체의 메서드이고, 다른 하나는 세션 프로세스를 이용한 방법입니다.

### 구조체의 이벤트 메서드를 이용한 방법:

* `BeforeInsert()`

이 메서드는 데이터베이스에 데이터를 삽입하기 전에 insert 프로세스에 의해 호출됩니다.

* `BeforeUpdate()`

이 메서드는 데이터베이스에 데이터를 업데이트하기 전에 update 프로세스에 의해 호출됩니다.

* `BeforeDelete()`

이 메서드는 데이터를 삭제하기 전에 delete 프로세스에 의해 호출됩니다.

* `func BeforeSet(name string, cell xorm.Cell)`

이 메서드는 Get 이나 Find 메서드가 데이터베이스에서 데이터와서 구조체에 할당하기 전에 호출됩니다.

* `func AfterSet(name string, cell xorm.Cell)`

이 메서드는 Get 이나 Find 메서드가 데이터베이스에서 데이터와서 구조체에 할당한 후에 호출됩니다.

* `AfterInsert()`

이 메서드는 데이터베이스에 데이터를 삽입한 뒤에 insert 프로세스에 의해 호출됩니다.

* `AfterUpdate()`

이 메서드는 데이터베이스에 데이터를 업데이트한 뒤에 update 프로세스에 의해 호출됩니다.

* `AfterDelete()`

이 메서드는 데이터를 삭제한 뒤에 delete 프로세스에 의해 호출됩니다.


### 프로세스 임시 이벤트를 이용한 방법:

* `Before(beforeFunc interface{})`

이 메서드는 모든 프로세스 이전에 호출됩니다. 예제:

```Go
before := func(bean interface{}){
    fmt.Println("before", bean)
}
engine.Before(before).Insert(&obj)
```

* `After(afterFunc interface{})`

이 메서드는 모든 프로세스 이후에 호출됩니다. 예제:

```Go
after := func(bean interface{}){
    fmt.Println("after", bean)
}
engine.After(after).Insert(&obj)
```
