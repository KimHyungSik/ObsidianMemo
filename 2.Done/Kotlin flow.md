### 날짜 : 2022-08-10
### 주제 : #Kotlin #Flow
----
### 정리
state flow, flow 차이
StateFlow : MutableStateFlow 와 StateFlow로 생성가능한 hot flow입니다. value속성을 통해 상태값을 읽고 collect를 통해 데이터를 수집합니다.StateFlow 와 LiveData는 비슷하게 사용 되지만 다른 점이 있다.
- `StateFlow`의 경우 초기 상태를 생성자에 전달해야 하지만 `LiveData`의 경우는 전달하지 않습니다.
-   뷰가 `STOPPED` 상태가 되면 `LiveData.observe()`는 소비자를 자동으로 등록 취소하는 반면, `StateFlow` 또는 다른 흐름에서 수집하는 경우 자동으로 수집을 중지하지 않습니다. 동일한 동작을 실행하려면 `Lifecycle.repeatOnLifecycle` 블록에서 흐름을 수집해야 합니다.

### 참고
- [Kotlin StateFlow 및 SharedFlow](https://developer.android.com/kotlin/flow/stateflow-and-sharedflow) 

### 연결된 메모
- 