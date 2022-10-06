### 날짜 : 2022-08-10
### 주제 : #Android #Compose #Navigation
----
### 정리
NavController를 중심으로 네이게이션, 백 스택등을 관리 하며 `rememberNavController()` 를 통해 NavController를 생성하여 사용 한다. 
```
val navController = rememberNavController()
```
navigation 동작을 실행하는 NavController와 그래프 역할을 하는 NavHost를 통해 Navigation동작을 실행 할 수 있다.
```
NavHost(navController = navController, startDestination = "profile") {    composable("profile") { Profile(/*...*/) }    composable("friendslist") { FriendsList(/*...*/) }    /*...*/}
```
compose간의 이동은 navigate()메서드를 통해 이동 가능하다.
### 참고
- [Compose 탐색](https://developer.android.com/jetpack/compose/navigation?hl=ko)

### 연결된 메모
- [[Android JetPack Compose 정의]]