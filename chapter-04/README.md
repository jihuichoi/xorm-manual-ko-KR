## 4. 데이터 삽입

Insert 메서드를 이용하여 레코드를 삽입하기 

* 레코드 1개 삽입하기

```Go
user := new(User)
user.Name = "myname"
affected, err := engine.Insert(user)
```

`Id` 칼럼이 자동 증가(autoincremen) 칼럼이면 삽입 후에 `user.Id` 칼럼은 자동으로 값이 채워집니다.

```Go
fmt.Println(user.Id)
```

* 테이블에 슬라이스로 된 여러 레코드 삽입하기

```Go
users := make([]User, 1)
users[0].Name = "name0"
...
affected, err := engine.Insert(&users)
```

* 테이블에 포인터 슬라이스로 된 여러 레코드 삽입하기

```Go
users := make([]*User, 1)
users[0] = new(User)
users[0].Name = "name0"
...
affected, err := engine.Insert(&users)
```

* 두 테이블에 레코드 1개 삽입하기

```Go
user := new(User)
user.Name = "myname"
question := new(Question)
question.Content = "whywhywhwy?"
affected, err := engine.Insert(user, question)
```

* 여러 테이블에 여러 레코드 삽입하기

```Go
users := make([]User, 1)
users[0].Name = "name0"
...
questions := make([]Question, 1)
questions[0].Content = "whywhywhwy?"
affected, err := engine.Insert(&users, &questions)
```

* 여러 레코드에 1개 이상의 레코드 삽입하기

```Go
user := new(User)
user.Name = "myname"
...
questions := make([]Question, 1)
questions[0].Content = "whywhywhwy?"
affected, err := engine.Insert(user, &questions)
```

알림: 트랜젝션이 포함된 삽입을 하려면 삽입 전에 `session.Begin()` 를 사용해야 합니다.
