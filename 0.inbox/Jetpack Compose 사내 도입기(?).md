### 날짜 : 2022-11-19
### 주제 : #Android #Compose #GDG
----
### 정리
도입 하게된 계기 
	xml + Koltin(Java)와 같이 UI와 로직을 따로 구현해야 하고 데이터를 View에 매핑하는 과정이 꼭 필요하고 이과정에서 실수가 발생하기 쉽다.

마이그레이션 - 상호 운용성 
- 전체화면 : Xml를 그냥 Compose로 작성
- 화면 일부 : ComposeView(xml View에서 Compose사용), AbstractComposeView(Compose -> View)

숙련도를 요구한다.
- Recomposition
- SideEffects 에대한 지식을 요구

### 참고
- JetpackCompose WokrSpaces 

### 연결된 메모
- 