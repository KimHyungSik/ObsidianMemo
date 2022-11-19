### 날짜 : 2022-11-19
### 주제 : #Andorid #MVI
----
### 정리
MVVM을 사용하면서
	기존의 MVVM과 관련하여 작업을 하다보면 하나의 State를 다양한 로직에서 관여하다 보니 코드의 복잡성과 Staet관리에서 실수할 가능성이 높아 지게된다. 옵저빙 하는 코드가 다양한 위치에서 파편화 되다보니 유지보수에서 문제를 찾을 수 있었다.

State란 무엇인가?
	"화면에서 보이는 모든 것" - 헤네스 도프만
	로딩상태, 데이터 호출성공, 실패 등등

단반향 아키텍처란?
	Event에 의해 매번 State를 생성하여 최신 UI에 반영한다.
	State는 **불변**으로 애플리케이션 상태를 보장한다.
	DataLayer에서 오는 데이터를 UiState로 래핑하여 View에 반영 된다.
	loading, bookmarks, error을 따로 옵정빙 하기보다는 State를 옵저빙하여 VIew에 반영하는 방법을 사용할 수 있다.
	장점
		하나의 State로 관리하여 관리가 편하다.

Redux란?
	복잡한 State를 관리하는데 탁월
	협업시 동료들과 State관리가 편하다
	JavaScript에서 있던 State관리 개념

Reduser
	Java에 있던 개념으로 
	User의 Action을 받아서 State에 값을 누적시키는 역활로 활용할 수 있다.

MVI란 무엇인가
Intent
	

### 참고
- 

### 연결된 메모
- 