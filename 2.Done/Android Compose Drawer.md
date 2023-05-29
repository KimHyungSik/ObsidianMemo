### 날짜 : 2023-05-29
### 주제 : #Android #Compose #SideMenu
----
### 정리
Drawer 란 앱들을 보면 사이드에서 나와 다른 페이지로 갈수 있는 목록을 보여주는 화면을 그릴 때 사용을 한다.
![[Pasted image 20230529221105.png]]
구현 방법은 생각 보다 간단하다.
Scaffold에 사용할 drawer를 추가한다.
rememberScaffoldState의 drawerState 의 open을 사용해주면 된다. (open 함수는 suspend함수이기 때문에 CoroutineScope에서 돌여야한다.)
```Kotlin
val scaffoldState = rememberScaffoldState()
 Scaffold(        
	 scaffoldState = scaffoldState,
	 drawerContent = {       
		 CraneDrawer()        
	 }   
)
```

### 참고
- [Navigation Drawer 구현 방법](https://developer88.tistory.com/entry/Navigation-Drawer-%EA%B5%AC%ED%98%84%EB%B0%A9%EB%B2%95-Jetpack-Compose)

### 연결된 메모
- 