### 날짜 : 2023-06-04
### 주제 : #Andorid #Compose #State
----
### 정리
기존에 Flow -> State를 변환 하기위해서 collectAsState()를 사용하였습니다.
만약 State -> Flow로 변화하기 위해서 snapshotFlow를 사용합니다.

```Kotlin
class EditableUserInputState(private val hint: String, initialText: String) {  
    var text by mutableStateOf(initialText)
	    private set
}

val currentOnDestinationChange by rememberUpdatedState(newValue = onToDestinationChanged)  
	//Flow Coroutine 처리를 위한 LaunchedEffect
	LaunchedEffect(editableUserInputState){  
		// editableUserInputState.text(State) -> Flow
	    snapshotFlow { editableUserInputState.text }  
	        .filter { !editableUserInputState.isHint }  
	        .collect {  
	            currentOnDestinationChange(editableUserInputState.text)  
	        }  
}
```

### 참고
- 

### 연결된 메모
- [[AndroidCompse State]]