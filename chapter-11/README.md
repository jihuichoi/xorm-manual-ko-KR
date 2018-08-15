## 내장 LRU 메모리 캐시 제공자

1. 글로벌 캐시

xorm 은 캐시를 지원합니다. 하지만 사용안함을 기본값으로 합니다. 이를 사용하려면:

```Go
cacher := xorm.NewLRUCacher(xorm.NewMemoryStore(), 1000)
engine.SetDefaultCacher(cacher)
```

일부 테이블의 캐시만 사용 중지를 하려면:

```Go
engine.MapCacher(&user, nil)
```

2. 테이블 캐시

일부 테이블에만 캐시를 사용하려면:

```Go
cacher := xorm.NewLRUCacher(xorm.NewMemoryStore(), 1000)
engine.MapCacher(&user, cacher)
```

주의:

1. 캐시가 활성화된 상태에서 Cols 메서드를 사용하면, 모든 칼럼값이 반환됩니다.

2. Exec 메서드를 사용한 뒤에는 캐시를 삭제해야 합니다.：

```Go
engine.Exec("update user set name = ? where id = ?", "xlw", 1)
engine.ClearCache(new(User))
```

캐시 구현 이론은 아래와 같습니다.

![cache design](https://raw.github.com/go-xorm/xorm/master/docs/images/cache_design.png)
