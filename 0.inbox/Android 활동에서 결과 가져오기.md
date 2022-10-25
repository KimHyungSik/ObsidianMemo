### 날짜 : 2022-10-25
### 주제 :
----
### 정리
새로운 Activity을 활성화 하여 Result를 받아오는 방법으로 `registerForActivityResult를` 사용하여 콜백을 등록할 수 있다. `registerForActivityResult는` `ActivityResultLauncher를` 반환하고 `ActivityResultLauncher는` ActivityREsultCallback을 사용할 수 있게 해준다.
기본적으로 다른 Activity를 등록하고 Callback을 받기위해서는 `registerForActivityResult`에 `StartActivityForResult()`를 추가하고 `ActivityResult`타입의 Callback을 받을 수 있다.
```Kotlin
class MainActivity : AppCompatActivity() {  
  
    val requestActivity: ActivityResultLauncher<Intent> = registerForActivityResult(  
        ActivityResultContracts.StartActivityForResult()  
    ){  
  
    }    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
        val selectButton = findViewById<Button>(R.id.select_button)  
        selectButton.setOnClickListener {  
            requestActivity.launch(Intent(baseContext, MainActivity2::class.java))  
        }  
    }  
}
```


## Contract 정의하기

Contract를 만들기 위해서는 ActivityResultContract<I, O>라는 추상 클래스를 상속한 서브클래스를 생성해야 한다. ActivityResultContract는 다음 두가지 추상 메서드를 가지고 있다.

abstract class ActivityResultContract<I, O> {    abstract Intent createIntent(@NonNull Context context, I input);    abstract O parseResult(int resultCode, @Nullable Intent intent);}

-   **createIntent 메서드** : 다른 액티비티를 호출하기 위한 Intent를 생성한다. 제네릭 타입 I가 intent를 생성하기 위한 매개변수 타입으로 전달된다. **(startActivityForResult 메서드 호출을 대체한다.)**
-   **parseResult 메서드** : 액티비티로 전달받은 결과 데이터를 제너릭 O타입으로 변환한다. **(onActivityResult 콜백 메서드 처리를 대체한다.)**

### 참고
- [Android Developer](https://developer.android.com/training/basics/intents/result?hl=ko)
- [ 액티비티 결과 처리하기](https://charlezz.medium.com/%EC%95%A1%ED%8B%B0%EB%B9%84%ED%8B%B0-%EA%B2%B0%EA%B3%BC-%EC%B2%98%EB%A6%AC%ED%95%98%EA%B8%B0-good-bye-startactivityforresult-onactivityresult-82bafc50edac)

### 연결된 메모
- 