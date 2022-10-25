### 날짜 : 2022-10-25
### 주제 : #Android #ResultForActivity
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
```Java
abstract class ActivityResultContract<I, O> {    
	abstract Intent createIntent(@NonNull Context context, I input);    
	abstract O parseResult(int resultCode, @Nullable Intent intent);
}
```
-   **createIntent 메서드** : 다른 액티비티를 호출하기 위한 Intent를 생성한다. 제네릭 타입 I가 intent를 생성하기 위한 매개변수 타입으로 전달된다. **(startActivityForResult 메서드 호출을 대체한다.)**
-   **parseResult 메서드** : 액티비티로 전달받은 결과 데이터를 제너릭 O타입으로 변환한다. **(onActivityResult 콜백 메서드 처리를 대체한다.)**


```Kotlin
class MainActivity : AppCompatActivity() {  
    class MainActivity2Contract : ActivityResultContract<String, String?>(){  
        override fun createIntent(context: Context, input: String): Intent {  
            return Intent(context, MainActivity2::class.java).apply {  
                putExtra("input", input)  
            }  
        }  
  
        override fun parseResult(resultCode: Int, intent: Intent?): String? {  
            return when(resultCode){  
                Activity.RESULT_OK -> intent?.getStringExtra("result")  
                else -> null  
            }  
        }    
	}  
        
    val launcher: ActivityResultLauncher<String> = registerForActivityResult(MainActivity2Contract()){  
  
    }  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
        val selectButton = findViewById<Button>(R.id.select_button)  
        selectButton.setOnClickListener {  
            launcher.launch("MainActivity")  
        }  
    }  
}
```
```
GetContent 이외에 현재 기 정의된 Contract는 다음과 같다.

-   GetContent : 사용자가 선택한 콘텐트의 Uri를 반환한다.
-   GetMultipleContent : 사용자가 선택한 1개 이상의 콘텐츠들이 List<Uri>형태로 반환된다.
-   TakePicturePreview : 사진을 찍고 Bitmap을 반환한다.
-   TakePicture : 촬영한 사진을 지정한 경로에 저장하고 Bitmap을 반환한다.
-   TakeVideo : 촬영한 비디오를 지정한 경로에 저장하고 썸네일을 Bitmap으로 반환한다.
-   CreateDocument : 새로운 문서 작성하고 해당 경로를 Uri형태로 반환한다.
-   OpenDocument : 사용자가 선택한 문서의 Uri를 반환한다.
-   OpenMultipleDocuments : 사용자가 선택한 1개 이상의 문서들이 List<Uri> 형태로 반환된다.
-   OpenDocumentTree : 사용자가 선택한 디렉토리의 Uri를 반환한다.
-   PickContact : 사용자가 선택한 연락처의 Uri를 반환한다.
-   RequestPermission : 단일 권한을 요청하고, 승인 여부를 반환한다.
-   RequestMultiplePermissions : 다중 권한을 요청하고, 승인 여부를 Map<String,Boolean>형태로 반환한다.
-   StartActivityForResult : 요청한 인텐트를 통해 액티비티를 실행하고, 액티비티 결과를 ActivityResult로 래핑하여 반환한다.
```

### 참고
- [Android Developer](https://developer.android.com/training/basics/intents/result?hl=ko)
- [ 액티비티 결과 처리하기](https://charlezz.medium.com/%EC%95%A1%ED%8B%B0%EB%B9%84%ED%8B%B0-%EA%B2%B0%EA%B3%BC-%EC%B2%98%EB%A6%AC%ED%95%98%EA%B8%B0-good-bye-startactivityforresult-onactivityresult-82bafc50edac)

### 연결된 메모
- 