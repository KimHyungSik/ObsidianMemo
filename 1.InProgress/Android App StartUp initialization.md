### 날짜 : 2023-05-13
### 주제 : #Andorid #startup 
----
### 정리
라브러리를 초기화 할때 어플리케이션의 Context를 필요로하는 경우가 있다. 이럴때 보통 ContentProvider를 사용하는데 ContentProvider의 경우에는 인스턴스화 비용이 많이 들고 그로인해 앱의 시작 속도가 늦춰진다.

Android AppStartUP을 이용하면 앱 시작시 dependency를 해결할 수 있다.

```kotlin
dependencies { 
	implementation "androidx.startup:startup-runtime:1.0.0-alpha01"
}
```

Initializer<*>를 재정의하여 사용한다.

-   **create()** : 컴포넌트를 초기화하는데 필요한 모든 동작을 포함하고 T 의 인스턴스를 리턴한다.
-   **dependencies()**
    -   Initializer 가 의존하는 다른 Initializer<> 객체의 목록을 리턴하도록 명시한다.
    -   이 메서드로 시작 시 앱이 Initializer 를 실행하는 순서를 제어할 수 있다.

```Kotlin
// Initializes WorkManager. 
class WorkManagerInitializer : Initializer<WorkManager> { 
	// context : application context 
	override fun create(context: Context): WorkManager { 
		val configuration = Configuration.Builder().build() 
		WorkManager.initialize(context, configuration) 
		return WorkManager.getInstance(context) 
	} 
	
	override fun dependencies(): List<Class<out Initializer<*>>> { 
		// No dependencies on other libraries. 
		return emptyList() 
	} 
}
```

### 참고
- [ANdroid](https://developer.android.com/topic/libraries/app-startup)
- [누군가의 블러그](https://kwongdevelop.tistory.com/33)

### 연결된 메모
- 