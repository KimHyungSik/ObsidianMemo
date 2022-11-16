### 날짜 : 2022-11-17
### 주제 : #Android #Compose #Codelap
----
### 정리
모든 Android 앱에서는 사용자에게 상태가 표시됩니다. 다음은 Android 앱 상태의 몇 가지 예시입니다.
-   채팅 앱에서 가장 최근에 수신된 메시지
-   사용자의 프로필 사진
-   항목 목록의 스크롤 위치
이벤트는 어떤 일이 발생했다고 프로그램 일부에 알려줍니다. 모든 Android 앱에는 다음과 같은 핵심 UI 업데이트 루프가 있습니다.

![f415ca9336d83142.png](https://developer.android.com/static/codelabs/jetpack-compose-state/img/f415ca9336d83142.png?hl=ko)

-   이벤트: 이벤트는 사용자 또는 프로그램의 다른 부분에 의해 생성됩니다.
-   상태 업데이트: 이벤트 핸들러가 UI에서 사용하는 상태를 변경합니다.
-   상태 표시: 새로운 상태를 표시하도록 UI가 업데이트됩니다.

**The Composition:** a description of the UI built by Jetpack Compose when it executes composables.
**Initial composition:** creation of a Composition by running composables the first time.
**Recomposition:** re-running composables to update the Composition when data changes.

### 참고
- 

### 연결된 메모
- 