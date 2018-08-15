# 자주 묻는 질문과 답(FAQ)

* xorm 태그와 json 태그를 같이 사용할 수 있습니까?

  빈 칸을 사용하세요.

```Go
type User struct {
    Name string `json:"name" xorm:"name"`
}
```

* xorm 에서 복합 기본 키(composite primary key)를 사용할 수 있습니까?

  네. pk 태그를 사용하세요. `pk` 태그를 가진 모든 필드를 하나의 기본 키로 사용합니다.(구조체의 필드 순서에 따릅니다.) 예제:

```
Id(xorm.PK{1, 2})`.
```

* 조인(join)은 어떻게 합니까?

  Join() 메서드와 extends 태그를 이용해 조인을 할 수 있습니다. 예제:

```
type Userinfo struct {
    Id int64
    Name string
    DetailId int64
}

type Userdetail struct {
    Id int64
    Gender int
}

type User struct {
    Userinfo `xorm:"extends"`
    Userdetail `xorm:"extends"`
}

var users = make([]User, 0)
err := engine.Table(&Userinfo{}).Join("LEFT", "userdetail", "userinfo.detail_id = userdetail.id").Find(&users)

//assert(User.Userinfo.Id != 0 && User.Userdetail.Id != 0)
```

User 구조체의 순서에 따라 조인 순서를 지정해야 합니다.(Userinfo -> Userdetail) 이 순서가 바르지 않으면, 같은 이름을 가진 필드에 잘못된 값이 들어갈 수 있습니다. 이런 경우 오류가 발생하지 않습니다.

조인 구문이 매우 길어질 경우 Sql() 메서드를 이용할 수 있습니다.

```
err := engine.Sql("select * from userinfo, userdetail where userinfo.detail_id = userdetail.id").Find(&users)

//assert(User.Userinfo.Id != 0 && User.Userdetail.Id != 0)
```

* 데이터베이스 시간대(timezone, time location)를 어떻게 설정합니까?

```Go
location, err = time.LoadLocation("Asia/Shanghai")
engine.TZLocation = location
```
