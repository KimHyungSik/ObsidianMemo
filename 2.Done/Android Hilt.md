### 날짜 : 2022-09-14
### 주제 : #Android #Hilt #DI 
----
### 정리
Hilt를 사용하기 위해서는 `@HiltAndroidApp`을 `Application`클래스에 추가 해야한다. `@HiltAndroidApp`어노테이션이 Hilt코드 생성을 트리거 한다.
다음으로 Android 프레임워크 클래스에서 사용하기 위해서는 `@AndroidEntryPoint`, `@HiltViewModel`를 사용한다. 
Hilt를 사용하여 구성요소를 받을 때는 `@Inject`를 사용 한다. 필드 삽입 또는 클래스 생성자에 사용 할 수 있다.
```Kotlin
@AndroidEntryPoint  
class ExampleActivity : AppCompatActivity() {  
	@Inject lateinit var analytics: AnalyticsAdapter  
	...  
}

class AnalyticsAdapter @Inject constructor(  
	private val service: AnalyticsService  
) { ... }
```

생성자가 외부에 있는 라이브러리나 인스턴스화 할 수 없는 인터페이스 같은 경우 Hilt모듈을 사용하여 주입을 구성 할 수 있다. `@Binds`를 이용하여 인터페이스를 간단하게 삽입 할 수 있습니다.
-   함수 반환 유형은 함수가 어떤 인터페이스의 인스턴스를 제공하는지 Hilt에 알려줍니다.
-   함수 매개변수는 제공할 구현을 Hilt에 알려줍니다.
```Kotlin
interface AnalyticsService {  
	fun analyticsMethods()  
}  

class AnalyticsServiceImpl @Inject constructor(  
	...  
) : AnalyticsService { ... }  
  
@Module  
@InstallIn(ActivityComponent::class)  
abstract class AnalyticsModule {  
	@Binds  abstract fun bindAnalyticsService(    
		analyticsServiceImpl: AnalyticsServiceImpl  
	): AnalyticsService  
}
```
`@Provides`같은 경우  클래스의 생성이 외부 라이브러리에서 될 경우 사용 할 수 있다.
-   함수 반환 유형은 함수가 어떤 유형의 인스턴스를 제공하는지 Hilt에 알려줍니다.
-   함수 매개변수는 해당 유형의 종속 항목을 Hilt에 알려줍니다.
-   함수 본문은 해당 유형의 인스턴스를 제공하는 방법을 Hilt에 알려줍니다. Hilt는 해당 유형의 인스턴스를 제공해야 할 때마다 함수 본문을 실행합니다.
```Kotlin
@Module  
@InstallIn(ActivityComponent::class)  
object AnalyticsModule {  
@Provides  fun provideAnalyticsService(    
	): AnalyticsService {      
	return Retrofit.Builder()               
		.baseUrl("https://example.com")               
		.build()               
		.create(AnalyticsService::class.java)  
	}  
}
```

Hilt로 여러 구성요소를 구성할때 동일한 유형에 대해 다르게 객체를 주입 하고 싶은경우가 있습니다. 그럴때는 어노테이션을 추가 구현하여 구분할 수 있습니다.
```Kotlin 
@Qualifier  
@Retention(AnnotationRetention.BINARY)  
annotation class AuthInterceptorOkHttpClient  
  
@Qualifier  
@Retention(AnnotationRetention.BINARY)  
annotation class OtherInterceptorOkHttpClient


@Module  
@InstallIn(SingletonComponent::class)  
object NetworkModule { 
	@AuthInterceptorOkHttpClient  
	@Provides  
	fun provideAuthInterceptorOkHttpClient(    
		authInterceptor: AuthInterceptor  
	): OkHttpClient {      
		return OkHttpClient.Builder()               
			.addInterceptor(authInterceptor)               
			.build()  
	}  
	
	@OtherInterceptorOkHttpClient  
	@Provides  
	fun provideOtherInterceptorOkHttpClient(    
		otherInterceptor: OtherInterceptor  
	): OkHttpClient {      
		return OkHttpClient.Builder()               
			.addInterceptor(otherInterceptor)               
			.build()  
	}  
}
```

Hilt로 객체를 삽입 할 때 `@InstallIn`주석에 참조하여 객체가 Android의 어떤 클래스에 결합할지 지정하여 사용 할 수 있습니다.
[Android 클래스용으로 생성된 구성요소](https://developer.android.com/training/dependency-injection/hilt-android#generated-components)
### 참고 
- [Android Developers](https://developer.android.com/training/dependency-injection/hilt-android)

### 연결된 메모
- [[Android Dagger]]