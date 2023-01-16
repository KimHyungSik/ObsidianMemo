### 날짜 : 2023-01-16
### 주제 : #Flutter #DI
----
### 정리
프로젝트가 커지면서 App 코들이 많아질 때 Widget들과 logic들을 분리하여 관리 해야 하는 상황이 생깁니다.
class들을 분리 할 때 의존성 관리를 신경쓰게 될 겁니다. 의존성 관리, 테스트 간편화 등의 이유로 프로젝트에 
Dependency Injection을 사용하는 경우는 많고 프레임워크에 따라 다양한 라이브러리가 존재 합니다.
Flutter에서는 GetIt이라는 Dependency Injection이 존재합니다.

그렇다면 왜 GetIt일까, 첫 번째로 상당히 빠릅니다. Pub.dev의 문서에는 GetIt의 속도는 O(1)로 Extremely fast라는 표현을 사용하고 있습니다. 두번째는 

### 참고
- [Pub.dev](https://pub.dev/packages/get_it)

### 연결된 메모
- 