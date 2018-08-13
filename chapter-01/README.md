# ORM 엔진 생성하기

xorm 을 사용하면, 하나 이상의 ORM 엔진을 생성할 수 있습니다. XORM 은 `Engine` 과 `EngineGroup` 을 지원합니다. `Engine` 은 한 개의 데이터베이스와 동작하며, `EngineGroup` 은 마스터/슬레이브 구조를 지원합니다. 이 둘은 비슷한 API를 제공하므로 쉽게 전환할 수 있습니다. 또한 전환을 위해 `EngineInterface`를 제공합니다.