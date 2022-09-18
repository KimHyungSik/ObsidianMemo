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
query를 추가하는 방법은 `queryParameters`에 map형태로 데이터를 전달 할 수 있고 body에 데이터를 추가하는 방법은 `data`에 map여


### 참고
-[Flutter Dio 간단정리 ](https://velog.io/@leeeeeoy/Flutter-Dio-%EA%B0%84%EB%8B%A8-%EC%A0%95%EB%A6%AC)
- [Pub.dev](https://pub.dev/packages/dio)

### 연결된 메모
- [[Flutter]]
- [[Flutter Retrofit]]