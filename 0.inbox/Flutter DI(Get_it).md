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

## 의존성 호출 방법
```Dart
var myAppModel = getIt<AppModel>();
var myAppModel = getIt.get<AppModel>()
var myAppModel = GetIt.instance<AppModel>();
```
미리생성한 또는 GitIt으로 가져온 instance로 필요한 타입의 의존성을 호출할 수 있다.

## 의존성 등록 방법
의존성을 주입할 객체는 일반적으로 앱의 시작 코드에서 GetIt에 객체 또는 객체를 생성할 함수를 등록 할 수 있습니다. GetIt에는 객체의 생명주기에 맞게 다양항 생성방버을 제공 하고 있습니다.
#### Factory
```Dart
void registerFactory<T>(FactoryFunc<T> func)
getIt.registerFactory<T>(() => func())
```
registerFactory은 객체를 생성하는 함수를 인자로 받습니다. `<T>`를 호출 할 때 func() 함수를 통해 매번 새로운 객체를 생산하여 제공합니다.

Future 함수로 만들어서 main 함수에 앱시작전에 호출하는 방법이 있습니다.

### Singleton
```Dart
void registerSingleton<T>(T instance)
getIt.registerFactory<T>(T)
```
registerSingleton은 객체 자체를 인자로 받습니다. `<T>`를 호출 할 때 인자로 받은 객체를 바로 제공 합니다.

### LazySingleton
```Dart
void registerLazySingleton<T>(FactoryFunc<T> func)
getIt.registerLazySingleton<T>(() => func())
```
registerLazySingleton은 객체를 생서하는 함수를 인자로 받는 점에서 registerFactory와 동일해 보이지만 
registerLazySingleton에서는 `<T>`를 처음 호출할 때만 객체를 생성하고 이후에는 동일한 객체를 제공한다.
생성시 리소스가 많이드는 객체의 경우 사용할 때 생성 하는 편이 초기 설정 시 에 포퍼먼스를 증가 시킬 수 있습니다.

의존성 생성과정에서 의존성이 필요한 경우 getIt으로 바로 호출 제공이 가능하다. 이때 타입 추론이 가능 하다면 
타입을 작성 하지 않아도 된다.
```Dart
getIt.registerSingleton<CatRepository>(CatRepositoryImp(injector()));
```

### Named
의존성을 작성하다 보면 두개의 다른 객체이지만 같은 타입의 경우 이

### Scope


### 참고
- [Pub.dev](https://pub.dev/packages/get_it)

### 연결된 메모
- 