### 날짜 : 2022-12-08
### 주제 :
----
### 정리
Side-Effect : Compose function 외부에서 발생하는 앱 상태의 변화를 말합니다.
	Composble은 Side-Effect로 부터 free 해야 한다. compose에 변화를 주기위해서는 변경되는 param을 통해서만 재호출 해야하며 compose함수 내부에서 param에 영향을 주는 동작을 구현하면 안된다.
	compostion이 완료될때 side-effect을 처리하는 composable function을 지원합니다.
	 effect란, UI를 방출하지 않는 composable function입니다.

### LaunchedEffect
	Composable 함수중에 suspend function이 존재 하고 이런 suspend function을Compose내에서 호출 
	하기 위해서 LaunchedEffect API를 제공 합니다. 
	LaunchedEffect는 Compose의 생성 시(Compostion enter) launch 되고, Compose가 화면에서 사
	라지면(Compostion leave) cancel된다. 즉 Launch는 Composable의 lifecyle에 묶입니다.
key를 기준으로 key가 변경될때마다 LaunchedEffect의 suspend fun을 취소하고 재실행 합니다.
- 사용 법
Composable의 State가 바뀌게 되면 매번 새로운 리컴포지션이 일어나고 그럴때마다 LaunchedEffect가 새로 시작할 수 있다. 이를 피하기 위해서 LaunchedEffect에 Key를 넣어주고 이 Key가 변경 될때에만 LaunchedEffect를 재실행 하게 할 수있다.
```Kotlin
LaunchedEffect(key){
	suspend function()
}
```

### rememberCoroutineScope
	LaunchedEffect의 LaunchedScope는 composable function에서 사용이 가능하기때문에 
	composable용 coroutine scope를 얻기 위해 rememberCoroutineScope를 사용 해야한다.
	LaunchedEffect와 동일하게 compose의 lifecycle에 따른다.

### rememberUpdatedState
	LaunchedEffect를 사용하는 시점에 lambda capturing의로 값들이 final로 들어가게된다. 하지만
	LaunchedEffect외부에서 변경된 값을 사용하고 LaunchedEffect를 재시작 시키지 않고 어떻게
	변경되는 값을 사용할 수 있을까. rememberUpdatedState를 한번 wrapping하여 값을 변동한다면 위와
	같은 동작이 가능하다.

### DisposableEffect
	side-effects를 처리하는 도중에 compose의 사태가 변경될때 특정 resource에대한 해재가 필요할때 
	DisposableEffect를 사용한다. 
	즉 LaunchedEffect와 동일하나, 재시작으로 인한 취소나 Compose leave로 인한 종료 
	시 onDispose {..} 구문이 항상 호출됩니다.DisposableEffect는 반드시 onDispose 구문을 구현해야 
	하며, 미구현시 Compile error가 발생합니다. 만약 onDispose의 block을 비운채로 구현하는 형태의 코드
	가 생긴다면 이는 다른 effect로 교체하는 게 좋습니다.

### SideEffect
	Composition이 성공적으로 이루어진 경우에 호출 됩니다. 종료 시점은 따로 없으며 recomposition이 이러 
	날때마다 발생하므로 사용시 유의 해야합니다.

### produceState
	producesState는 Compose상태로 만들어서 State<T>를 반환 하게 도와줍니다.
	추가적으로 suspend fun을 non-suspending하게 처리하여 State를 관리할 수 있게 할 수 있습니다.

### derivedStateOf
	MediatorLiveData의 기능과 비슷 하며 여러개의 State변경을 trigger삼아 자신의 상태를 변경 할 
	수있습니다.
Saver
rememberupdateState


### 참고
- [Medium](https://medium.com/hongbeomi-dev/jetpack-compose-doc-%EC%9D%BD%EA%B8%B0-part1-%EA%B8%B0%EC%B4%88-9a11fd0327cc)
- [투덜이의 리얼 블로그](https://tourspace.tistory.com/412)

### 연결된 메모
- 
