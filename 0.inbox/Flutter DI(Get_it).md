### 날짜 : 2023-01-16
### 주제 : #Flutter #DI
----
### 정리
프로젝트가 커지면서 App 코들이 많아질 때 Widget들과 logic들을 분리하여 관리 해야 하는 상황이 생깁니다.
class들을 분리 할 때 의존성 관리를 신경쓰게 될 겁니다. 의존성 관리, 테스트 간편화 등의 이유로 프로젝트에 
Dependency Injection을 사용하는 경우는 많고 프레임워크에 따라 다양한 라이브러리가 존재 합니다.
Flutter에서는 GetIt이라는 Dependency Injection이 존재합니다.

그렇다면 왜 GetIt일까, 첫 번째로 상당히 빠릅니다. Pub.dev의 문서에는 GetIt의 속도는 O(1)로 Extremely fast라는 표현을 사용하고 있습니다. 두 번째는 러닝커브가 낮다 입니다. 밑에서 사용법을 소개 하겠지만 상당히 간단히 Dependency Injection을 구현 할 수 있습니다. 세 번째로는 Factory, Singleton, LazySingleton 등 다양한 Dependency Injection방법을 제공 하고 있어 필요에 맞게 사용 할 수 있습니다.

## GetIt 시작 방법
이제 GetIt의 사용법을 알아 봅시다. Dart에서는 전역 변수 사용을 지원하고 있습니다. GetIt의 추천 사용 방법으로 GetIt을 전역 변수로 생성하여 사용하는 방법을 예시로 사용하고 있습니다. 하지만 프로젝트 구조상 변수에 접근하지 못하더라도 GetIt.instance로 생성된 GetIt 객체는 Singleton으로 구현되어 있어 필요에 따라 추가 생성하여 사용할 수 있습니다.
```Dart
GetIt getIt = GetIt.instance;
```

## 의존성 등록 방법
의존성을 주입할 객체는 일반적으로 앱의 시작 코드에서 GetIt에 객체 또는 객체를 생성할 함수를 등록 할 수 있습니다. GetIt에는 객체의 생명주기에 맞게 다양항 생성방버을 제공 하고 있습니다.
#### Factory
```Dart
void registerFactory<T>(FactoryFunc<T> func)
getIt.registerFactory<T>(() => func())
```
factory는 객체를 새성하는 함수를 인자로 받습니다. `<T>`를 호출할 때 func() 함수를 통해 매번 새로운 객체를 생산하여 제공합니다.

### Singleton
```Dart
void registerSingleton<T>(T instance)
```


### 참고
- [Pub.dev](https://pub.dev/packages/get_it)

### 연결된 메모
- 