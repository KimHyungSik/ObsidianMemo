### 날짜 : 2022-10-12
### 주제 : #Rxjava #Rxkotlin #BehaviorProcessor #PublishProcessor
----
### 정리
 PublishProcessor
 - 구독 시점 이전에 발행된 데이터는 무시하고, 구독 시점 이후에 발행된 데이터를 발행하는 Processor
 - 데이터를 유지하는 기능은 없으며 기본적으로 브릿지 역활로 사용 됨
 ![[Pasted image 20221013003756.png]]

BehaviorProcessor
-   구독 시점 이전에 발행된 데이터 중 가장 최근에 발행된 데이터 하나만 발행하고, 구독 시점 이후에 발행된 데이터를 발행하는 Processor
-   `createDefault` 메소드를 활용하여, 이전에 발행된 데이터가 없을 시 기본적으로 방출 할 데이터를 정할 수 있음, 데이터를 유지하는 기능이 있다.
![[Pasted image 20221013003838.png]]

AsyncProcessor
-  데이터 발행이 완료되면, 데이터 발행 완료 직전에 발행된 데이터만 발행하는 Processor
-  마지막 데이터만 반환 한다고 생각하면 될 것같음
![[Pasted image 20221013004022.png]]

### 참고 자료
- 

### 연관된 기술
- [[Cold Publisher vs Hot Publisher]]
- [[Rxjava Processor vs Subject]]