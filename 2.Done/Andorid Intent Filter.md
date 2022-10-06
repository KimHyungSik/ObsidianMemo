### 날짜 : 2022-08-10
### 주제 : #Android #Intent #Intent-filter
----
### 정리
암시적 인텐트를 사용할 경우 매니페스트 파일에 선언된 인텐트 필터를 통과한 경우 암시적 인테트를 앱의 구성 요소에 전달 한다
- <action> : name 특성 허용된 인텐트 작업을 선언 한다.
- <data> : 허용된 데이터 유형을 선언 (`scheme`, `host`, `port`, `path`)
- <category> : name에서 허용된 인텐트의 카테고리를 선언한다.
Android시스템은 매니페스트 파일에 선언된 필터를 테스트 하여 통과 해야 구성요소에 인텐트를 전달 한다.

### 참고
- [Android Intent Filter](https://developer.android.com/guide/components/intents-filters)

### 연결된 메모
- [[Android JetPack Compose DeepLink]]
- [[Android Intent]]