### 날짜 : 2022-11-19
### 주제 : #Andorid #Coroutine #GDG
----
### 정리
Coroutine : 실행을 일시 중지하고 재개할 수 있도록 비선점형 멀티태스킹을 일반화하는 프로그램 요소

Kotlin Coroutine
- Suspend function
	- Coroutine이 중단할 수 있는 함수
	- suspend함수는 suspend 또는 scope안에서 사용가능
- Scope
	- Convention for structured concurrency
		- 코루틴 계층의 추적 및 취소 전파 가능한 Job 포함
		- 메모리 관리에 용이
	- Builder
		- 코루틴을 생성하기 위해 사용(runBlocking, launch, async...등)
	- Context
		- Set of element
		- Job
			- Coroutine을 식별하고 수명주기를 관리할 때사용
			- Coroutine의 상태를 확인 할때도 사용할 수 있다.
			- Coroutine의 계층을 취소, 에러 전파
				- 부모에서 취소되면 자식들을 모두 취소
					- 자식은 자기만 취소
				- 자식에서 에러가 발생하면 부모의 모든 자식을 취소

### async, Launch
Async
- Deferred를 반환
- await() 힘수를 이용하여 결과값을 얻을 수 있다.
Launch
- Job을 반환한다.
- join() 함수로 기다릴수 있다

### Job, Cancellation
- 부모가 취소된다면 자식의 Coroutine들도 모두 취소 된다.
withContext(NonCancellable)

### Exceptions handling
- 자식 중에 에러가 발생하면 부모에게 알리고 모든 자식을 취소 시킴
- SupervisorJob
	- 해당 잡이 부모이면, 에러난 자식하나만 취소시킴
	- supervisorScope도 사용 가능
- try{} catch{}
- CoroutineExcpetionHandler : 에러처리를 미리 정의 하고 launch시에 handle을 넣어 준다.

### Dispatcher
 - Coroutine실행시 어떤 스레드를 사용할지 지정할 수 있다.


### 참고
- 

### 연결된 메모
- 