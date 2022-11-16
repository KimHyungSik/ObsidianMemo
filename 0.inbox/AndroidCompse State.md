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

**Compose에는 특정 상태를 읽는 컴포저블의 리컴포지션을 예약하는 특별한 상태 추적 시스템이 있습니다**.
Compose의 [`State`](https://developer.android.com/reference/kotlin/androidx/compose/runtime/State?hl=ko) 및 [`MutableState`](https://developer.android.com/reference/kotlin/androidx/compose/runtime/MutableState?hl=ko) 유형을 사용하여 Compose에서 상태를 관찰할 수 있도록 합니다.
```Kotlin
val count: MutableState<Int> = mutableStateOf(0)
```

이를 위해 구성 가능한 인라인 함수 [`remember`](https://developer.android.com/reference/kotlin/androidx/compose/runtime/package-summary?hl=ko#remember(kotlin.Function0))를 사용할 수 있습니다. `remember`로 계산된 값은 _초기 컴포지션_ 중에 컴포지션에 저장되고 저장된 값은 리컴포지션 간에 유지됩니다.
일반적으로 `remember`와 `mutableStateOf`는 구성 가능한 함수에서 함께 사용됩니다.
[Compose 상태 문서](https://developer.android.com/jetpack/compose/state?hl=ko#state-in-composables)에 설명된 대로 이를 작성하는 몇 가지 유사한 방법은 다음과 같습니다.
```Kotlin
 val count: MutableState<Int> = remember { mutableStateOf(0) }
```
**by** 키워드를 사용하여 `count`를 var로 정의할 수 있습니다. 위임의 getter 및 setter 가져오기를 추가하면 매번 `MutableState`의 `value` 속성을 명시적으로 참조하지 않고도 `count`를 간접적으로 읽고 변경할 수 있습니다.
```Kotlin
 var count by remember { mutableStateOf(0) }
```

[`remember`](https://developer.android.com/reference/kotlin/androidx/compose/runtime/package-summary?hl=ko#remember(kotlin.Function0))는 컴포지션에 객체를 저장하고, `remember`가 호출되는 소스 위치가 리컴포지션 중에 다시 호출되지 않으면 객체를 삭제합니다. `remember`를 사용하면 리컴포지션 간에 상태를 유지하는 데 도움이 되지만 **구성 변경 간에는 유지되지 않습니다**. 이를 위해서는 `remember` 대신 [`rememberSaveable`](https://developer.android.com/reference/kotlin/androidx/compose/runtime/saveable/package-summary?hl=ko#rememberSaveable(kotlin.Array,androidx.compose.runtime.saveable.Saver,kotlin.String,kotlin.Function0))을 사용해야 합니다.
`rememberSaveable`은 [`Bundle`](https://developer.android.com/reference/android/os/Bundle?hl=ko)에 저장할 수 있는 모든 값을 자동으로 저장합니다. 다른 값의 경우에는 맞춤 Saver 객체를 전달할 수 있습니다. [Compose에서 상태 복원](https://developer.android.com/jetpack/compose/state?hl=ko#restore-ui-state)에 관한 자세한 내용은 문서를 참고하세요.

`remember`를 사용하여 객체를 저장하는 컴포저블에는 내부 상태가 포함되어 있어 컴포저블을 `스테이트풀(Stateful)`로 만듭니다. 이는 호출자가 상태를 제어할 필요가 없고 상태를 직접 관리하지 않아도 상태를 사용할 수 있는 경우에 유용합니다. 그러나 **내부 상태를 갖는 컴포저블은 재사용 가능성이 적고 테스트하기가 더 어려운 경향이 있습니다**. **상태를 보유하지 않는 컴포저블을 스테이트리스(Stateless) 컴포저블이라고 합니다**. 상태 끌어올리기를 사용하면 **스테이트리스(Stateless)** 컴포저블을 쉽게 만들 수 있습니다.

- **스테이트리스(Stateless)** 컴포저블은 상태를 소유하지 않는 컴포저블입니다. 즉, 새 상태를 보유하거나 정의하거나 수정하지 않습니다.
- **스테이트풀(Stateful)** 컴포저블은 시간이 지남에 따라 변할 수 있는 상태를 소유하는 컴포저블입니다.

### 참고
- 

### 연결된 메모
- 