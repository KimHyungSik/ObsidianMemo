### 날짜 : 2022-08-10
### 주제 : #Navigation , #Compose , #DeepLink
----
### 정리
Jetpack Compose Navigation Codelab을 정리한 자료 입니다.

Compose에서 DeepLink를 사용 할려면 먼저 [[Andorid Intent Filter]]를 추가 합니다. 
```
<intent-filter>        
	<action android:name="android.intent.action.VIEW" />        
	<category android:name="android.intent.category.DEFAULT" />        
	<category android:name="android.intent.category.BROWSABLE" />        
	<data android:scheme="rally" android:host="accounts" />
</intent-filter
```

NavHost에 composable내부에 `deepLinks`를 추가 구현 해주면 바로 연결이 됩니다. `uriPattern`을 전달하는 intent-filter의 ==scheem://host== 의 링크로 구성해 줍니다
```
composable(    
	"$accountsName/{name}",    
	arguments = listOf(        
		navArgument("name") {            
			type = NavType.StringType        
		},    
	),    
	deepLinks =  listOf(navDeepLink {        
	uriPattern = "rally://$accountsName/{name}"    
	})
)
```
### 참고
- [Android Compose Navigation Codelab](https://developer.android.com/codelabs/jetpack-compose-navigation?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fcompose%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fjetpack-compose-navigation#4) 

### 연결된 메모
- [[Android JetPack Compose의 Navigation]]
- [[Andorid Intent Filter]]
