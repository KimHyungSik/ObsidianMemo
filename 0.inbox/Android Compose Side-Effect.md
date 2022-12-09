### 날짜 : 2022-12-08
### 주제 :
----
### 정리
Side-Effect : Compose function 외부에서 발생하는 앱 상태의 변화를 말합니다.
	Composble은 Side-Effect로 부터 free 해야 한다. compose에 변화를 주기위해서는 변경되는 param을 통해서만 재호출 해야하며 compose함수 내부에서 param에 영향을 주는 동작을 구현하면 안된다.
	compostion이 완료될때 side-effect을 처리하는 composable function을 지원합니다.
	 effect란, UI를 방출하지 않는 composable function입니다.

### LaunchedEffect
	Composable 함수중에 suspend function이 존재 하고 이런 suspend function을Compose내에서 호출 하기 위해서 LaunchedEffect API를 제공 합니다. 
	LaunchedEffect는 Compose의 생성 시(Compostion enter) launch 되고, Compose가 화면에서 사라지면(Compostion leave) cancel된다. 즉 Launch는 Composable의 lifecyle에 묶입니다.
- 사용 법
Composable의 State가 바뀌게 되면 매번 새로운 리컴포지션이 일어나고 그럴때마다 LaunchedEffect가 새로 시작할 수 있다. 이를 피하기 위해서 LaunchedEffect에 Key를 넣어주고 이 Key가 변경 될때에만 LaunchedEffect를 재실행 하게 할 수있다.
```Kotlin
LaunchedEffect(key){
	suspend function()
}
```

### rememberCoroutineScope
	LaunchedEffect의 LaunchedScope는 

DisposableEffect

Saver
rememberupdateState
produceState
derivedStateOf
### 참고
- 

### 연결된 메모
- 
