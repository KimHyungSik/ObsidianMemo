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
			- 

### 참고
- 

### 연결된 메모
- 