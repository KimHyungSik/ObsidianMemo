### 날짜 : 2022-10-13
### 주제 : #Rxjava 
----
### 정리
### Cold Publisher
- 구독자가 구독을 하는 시점에서 부터 데이터 발생하는 Publisher
-   구독자가 구독하는 시점에 데이터 발행을 시작하기 때문에, 모든 구독자는 동일한 데이터를 수신 받을 수 있음
-  앞서 살펴본 Single / Flowable / Observable 등이 이에 해당 됨

### Hot Publisher
-   구독자가 구독하지 않아도, 데이터를 방출하는 Publisher
-   구독자가 구독하지 않아도 데이터를 방출하기 때문에, 구독자가 구독하기 이전에 발행된 데이터는 구독자가 데이터를 받을 수 없음
-   Processor / Subject 등이 이에 해당 됨
-   중복된 이벤트 발행을 막기 위해 사용 할 수 있음 ( MultiCasting / UniCasting, 추후 포스팅에서 Connectable Observable과 함께 다룰 예정 )
- 
### 참고
- 

### 연결된 메모
- [[Rxjava Processor]]