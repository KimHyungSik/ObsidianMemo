### 날짜 : 2022-09-27
### 주제 : #gradle #buildSrc # DSL
----
### 정리
Kotlin DSL
- 장점
	- IDE가 지원하는 언어 환경, Kotlin의 경우 IDE가 지원하여 코드 탐색, 자동완성, 편한 변수 사용이 가능하다
	- 멀티모듈 사용시 의존성 관리가 편해진다
- 단점
	- Groovy DSL보다 느림
	- 새로운 라이브러리 및 안드로이드 프레임워크 도입시 불편하거나 미지원
buildSrc
>Gradle이 수행되면 buildSrc 디렉터리가 존재하는지 체크한다.  
이 경우 Gradle은 자동적으로 코드를 컴파일하고 테스트한 뒤 당신의 빌드 스크립트의 classpath에 넣는다.  
이 방법은 유지 보수, 리팩터링 및 코드 테스트가 더 쉽다.

KotlinDSL사용해보기
Android
### 참고
- [Kotlin DSL + buildSrc으로 의존성 관리](https://beomseok95.tistory.com/367)
- [# [Android] 멀티모듈에서 buildSrc + Kotlin DSL로 Dependency 관리하기](https://velog.io/@yuuuzzzin/Android-buildSrc-Kotlin-DSL%EB%A1%9C-Dependency-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0)

### 연결된 메모
- 