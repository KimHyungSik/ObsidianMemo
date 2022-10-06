### 날짜 : 2022-09-13
### 주제 : #Android #Dagger #DI
----
### 정리
Dagger기본 사항
```Kotlin
class UserRepository(    
private val localDataSource: UserLocalDataSource,    
private val remoteDataSource: UserRemoteDataSource  
) { ... }
```
`UserRepository` 클래스를 생성 할 때 Dagger가 생성방법을 알 수 있게 `@Inject` 를 추가 한다.
```Kotlin
class UserRepository @Inject constructor(    
private val localDataSource: UserLocalDataSource,    
private val remoteDataSource: UserRemoteDataSource  
) { ... }
```
`@Inject`를 달아 줍으로 Dagger가 UserRepository를 어떻게 인스턴스화 하는지 알게 됩니다.
다음으로 UserRepository를 Dagger의 구성요소로 만들기 위해 `@Component` 인터페이스에 추가 해야한다. Dagger는 종속 항목이 필요할때 `@Component` 인터페이스에서 구성 요소를 찾는다. 
```Kotlin
@Component  
interface ApplicationGraph {    
	fun repository(): UserRepository  
}
```

==Android 프레임워크 클래스==는 시스템에서 초기화 하기 때문에 Dagger가 자동으로 생성할 수 없다 그래서 클래스의 생성자에 `@Inject`를 사용 하는 대신 필드에서 `@Inject` 를 사용 한다. 
삽입되는 필드는 비공개로 유지할 수 없다. 최소한 package-private공개상태를 유지해야 한다.
```Kotlin
class LoginActivity: Activity() {    
	// You want Dagger to provide an instance of LoginViewModel from the graph    
	@Inject lateinit var loginViewModel: LoginViewModel  
}
```
`LoginActivity` 에 `LoginViewModel`을 제공하기 위해서는 @Component 인터페이스에 그래프를 등록해야 한다.
```Kotlin
@Component  
interface ApplicationComponent {    
// This tells Dagger that LoginActivity requests injection so the graph needs to    // satisfy all the dependencies of the fields that LoginActivity is requesting.  
	fun inject(activity: LoginActivity)  
}
```

모듈정의
 [Retrofit](https://square.github.io/retrofit/) 같이 기존의 인스턴스화 방법과 다른 방버으로 인스턴스를 생성해야 하는 경우 `@Module`를 사용할 수 있다. `@Module`내부에 `@Provides`주석을 사용하여 종속 항목을 정의 할 수 있다.
```Kotlin
@Module  
class NetworkModule {   
	@Provides    
	fun provideLoginRetrofitService(): LoginRetrofitService {      
		return Retrofit.Builder()                
			.baseUrl("https://example.com")                
			.build()                
			.create(LoginService::class.java)    
	}  
}
```
이후 `@Component`에 Module을 사용 할 수 있도록 등록 한다
```Kotlin
@Component(modules = [NetworkModule::class])  
interface ApplicationComponent {   
	...  
}
```
`@Singleton`생성 범위를 사용할 수 있다. Application 클래스에서 생성되면 앱이 소멸하면 소멸되므로 메모리 누수를 생각하며 범위를 지정하여 사용해야한다.

#### Dagger 하위 구성요소
`@Subcomponent`를 활용하면 Dagger의 하위 구성요소를 사용할 수 있다. LoginComponent를 `@Subcomponet`로 정의 하고 `inject`를 구성하여 저의 할 수 있다. 
```Kotlin
@Subcomponent  
interface LoginComponent {    

	@Subcomponent.Factory    
	interface Factory {        
		fun create(): LoginComponent   
	}    
	
	fun inject(loginActivity: LoginActivity)  
}
```
하위 구성을 구성하면 `@Module`에 추가하고 Component에 등록하여 하위구성에서 구현한 LoginComponent를 주입 받아 사용할 수 있게 된다.
```Kotlin
@Module(subcomponents = LoginComponent::class)  
class SubcomponentsModule {}

@Singleton  
@Component(modules = [NetworkModule::class, SubcomponentsModule::class])  
interface ApplicationComponent {  
}
```

### 참고 자료
- [Android Developers](https://developer.android.com/training/dependency-injection/dagger-android?hl=ko)
- [찰스의 안드로이드](https://www.charlezz.com/?p=1259)

### 연관된 기술
- 