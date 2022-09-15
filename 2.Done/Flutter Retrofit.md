### 날짜 : 2022-09-16
### 주제 : #Flutter #Network
----
### 정리
android에서 사용하던 retrofit과 사용방법이 유사하며 어노테이션을 통한 HTTP통신을 간편하게 구현할 수 있는 라이브러리이다.
엔드포인트 별 생성하고 싶은 메서드를 자동으로 생성하여 작업의 효율성이 좋다. Retrofit은 기본적으로 DIO를 통해 HTTP통신을 수행한다.(Android OkHttp와 비슷한 느낌)
```dart
@RestApi(baseUrl: "http://localhost:8080")
abstract class CharacterService {
	factory CharacterService(Dio dio) = _CharacterService;
	@GET("/character")
	Future<HttpResponse<CharacterResponse>> getCharacters(
		@Query("page") int page,
		@Queries() Map<String, String>? options,
	);

	@GET("/character/{id}")
	Future<HttpResponse<CharacterInfo>> getCharacter(@Path("id") int id);
}
```
`@RestApi`를 통해 Retrofit을 사용하는 클래스임과 baseUrl을 설정한다. 또는 
	Dio 객체를 생성할 때 baseUrl을 설정하면 `@ResApi`에서 baseUrl를 삭제할 수 있다.(기본적으로 baseUrl은 같기 때문에 Dio객체를 DI로 받을때 이 방법이 더 효율적인거 같다.)
`@GET`, `@POST`등의 HTTP method와 엔드포인트를 지정하여 메서드를 준비한다.

이후는 Dio 객체를 생성하여 `@RestApi`객체에 주입하면서 객체를 생성하고 내부 구현 메서드들을 사용할 수 있다.(안드로이드 Retrofit과 사용방법 동일)

어노테이션을 통헤 HTTP통신 클래스를 자동으로 생성해주며, 기존의 HTTP통신을 한번더 Wrapping한 패키지이다. 

### 참고
- [Pub.dev](https://pub.dev/packages/retrofit)

### 연결된 메모
- [[Flutter]]
- [[Flutter Dio]]