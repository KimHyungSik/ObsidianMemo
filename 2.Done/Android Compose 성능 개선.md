### 날짜 : 2022-08-11
### 주제 : #Compose #성능
----
### 정리
1. remember: 데이터의 변경 시 마다 Compose를 변경하는 가장 최적화된 방법이다
2. LazyList Key: Lazy를 사용 할 때 고유한 key를 제공하면 Lazy의 아이템이 다시 그려지는 문제를 해결 할 수 있다.
3. derivedState: 필요로하는 구성이 변경될때만 실질적으로 변경 된다(ex. LazyColumn에서 `firstVisibleitemIndex`의 0번쨰 아이템을 추척하는 경우)
4. Reading state: drawBehind를 사용하여 Draw단계만 재실행 할 수 있다.

### 참고
- [Jetpack Compose 성능 문제](https://www.youtube.com/watch?v=EOQB8PTLkpY&t=1202s)

### 연결된 메모
- [[Android JetPack Compose 정의]]
- [[Android Compose가 그려지는 방법]]