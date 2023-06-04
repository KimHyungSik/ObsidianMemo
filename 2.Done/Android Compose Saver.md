### 날짜 : 2023-06-04
### 주제 : #Andorid #Compse #State
----
### 정리
rememberSaveable은 Bundle이 가능한 타입에 대에서 지원하기 때문에 Bundle로 래핑할 수 없는 객체의 경우에는 Savedr를 구성하여 저장해야 한다.

```Kotlin
class EditableUserInputState(private val hint: String, initialText: String) {  
    var text by mutableStateOf(initialText)  
        private set  
    fun updateText(newText: String) {  
        text = newText  
    }  
  
    val isHint: Boolean  
        get() = text == hint  
  
    companion object{  
        val Saver: Saver<EditableUserInputState, *> = listSaver(  
            save = { listOf(it.hint, it.text) },  
            restore = {  
                EditableUserInputState(  
                    hint = it[0],  
                    initialText = it[1],  
                )  
            }  
        )  
    }}
    }
    
rememberSaveable(hint, saver = EditableUserInputState.Saver){  
    EditableUserInputState(hint, hint)  
}
```

### 참고
- 

### 연결된 메모
- [[AndroidCompse State]]