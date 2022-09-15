### 날짜 : 2022-08-10
### 주제 : #Intent
----
### 정리
Intent는 메시징 객체로 앱 구성 요서에 작업을 요청하는 데 사용할 수 있습니다. 사용 사례로 크게 3가지로 나뉜다
- 액티비티 시작
> Activity의 새로운 인스턴스를 시작하기위해 Intent를 startAtivity에 Intent를 전달한다.
- 서비스 시작
>일회성 작업을 수행하도록 하려면(예: 파일 다운로드) Intent 에 전달하면 됩니다. Intent 는 시작할 서비스를 설명하고 모든 필수 데이터를 담고 있습니다.
- 브로드캐스트 전달
> Intent를 sendBroadcast() 또는 sendOrderedBroadcast() 에 전달하면 다른 앱에 브로드캐스트를 전달할 수 있습니다.

인텐트의 유형은 두가지가 있습니다
- 명시적 인텐트 : 앱의 패키지 이름을 알고 시작하고자 하는 액티비티 또는 서비스의 클래스 이름을 알고 있을때 인텐트에 명시하여 액티비티 또는 서비스를 실행하는 것
- 암시적 인텐트 : 특정한 이름을 명시하지 않고 대신 수행할 작업을 선언하여 앱에서 구성요소가 이를 처리 할 수 있도록 작업하는 것 
암시적 인텐트를 사용하면 Android 시스템에서 시작할 적절한 요소를 앱의 매니페스트 파일에서 선언된 [[Andorid Intent Filter]]를 찾아 구성요소를 시작합니다.


### 참고
- [Android Intent](https://developer.android.com/guide/components/intents-filters)

### 연결된 메모
- [[Andorid Intent Filter]]