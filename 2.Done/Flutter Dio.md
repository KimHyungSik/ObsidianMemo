### 날짜 : 2022-09-16
### 주제 : #Flutter #Network 
----
### 정리
 http 처럼 서버와 통신을 하기 위해 필요한 패키지다.
 패키지 설정 방법
```
yaml
	dependencies:
	  dio: ^4.0.0
```
[Dev.pub](https://pub.dev/)에서 Dio 패키지의 사용방법을 보면 상단히 간단한걸 확인 할 수 있다.
```Kotlin
```dart
import 'package:dio/dio.dart';
void getHttp() async {
  try {
    var response = await Dio().get('http://www.google.com');
    print(response);
  } catch (e) {
    print(e);
  }
}
```
Dio객체를 생성하고 원하는 주소와 메서드로 HTTP를 호출 할 수 있다.
query를 추가하는 방법은 `queryParameters`에 map형태로 데이터를 전달 할 수 있고 body에 데이터를 추가하는 방법은 `data`에 map형태로 데이터를 추가 할 수 있다.
```Kotlin
```dart
var dio = Dio();

// 첫번째 방법
final response = await dio.get('/test?id=12&name=wendu');

// 두번째 방법
final response = await dio.get('/test', queryParameters: {'id': 12, 'name': 'wendu'});

// 세번째 방법
final response = await dio.request(
  '/test',
  data: {'id':12,'name':'xx'},
  options: Options(method:'GET'),
);

// post
final response = await dio.post('/test', data: {'id': 12, 'name': 'wendu'});
```
추가적으로 options를 제공하고 있는데. `baseUrl`, `connectTimeout`, `receiveTimeout`, `headers`등이 있다. dio또한 Android의 Okhttp작업시 유용했던 Interceptors를 제공 하고 있습니다(토큰 추가, 토큰검사, 로그깅 등등 구현 가능) 자세한 사용방법은 [Pub.dev #Interceptors](https://pub.dev/packages/dio#interceptors)에서 확인 가능하다.


### 참고
- [Flutter Dio 간단정리 ](https://velog.io/@leeeeeoy/Flutter-Dio-%EA%B0%84%EB%8B%A8-%EC%A0%95%EB%A6%AC)
- [Pub.dev](https://pub.dev/packages/dio)
- [Networking in Flutter using Dio](https://blog.logrocket.com/networking-flutter-using-dio/)

### 연결된 메모
- [[Flutter]]
- [[Flutter Retrofit]]