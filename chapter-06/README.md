## 6. Update

`Update` 메서드를 이용해 레코드의 값을 업데이트할 수 있습니다. 

첫번째 파라미터는 구조체 포인터나 `map[string]interface{}` 를 사용합니다. 구조체 포인터일 경우 non-empty 필드와 non-zero 필드만 업데이트됩니다. 그리고 `map[string]interface{}` 일때는 맵 키에 해당하는 칼럼의 값이 업데이트됩니다. 맵의 값은 업데이트될 값입니다.
	
`Update` 메서드는 두 개의 값을 반환합니다. 첫번째는 `영향받은(affected)` 레코드 수입니다.(`SQLITE` 에서는 업데이트 조건의 수만 반환합니다.)


```Go
user := new(User)
user.Name = "myname"
affected, err := engine.Id(id).Update(user)
```

0 값으로 업데이트하려면 다음 방법 중 하나를 사용합니다.

1. `Cols` 메서드로 0이나 빈 값으로 업데이트할 칼럼을 지정합니다.

```Go
affected, err := engine.Id(id).Cols("age").Update(&user)
```

2. `map[string]interface{}` 사용. 구조체 포인터나 문자열로 테이블을 지정해야 합니다.

```Go
affected, err := engine.Table(new(User)).Id(id).Update(map[string]interface{}{"age":0})
affected, err := engine.Table("user").Id(id).Update(map[string]interface{}{"age":0})
```
